# Gulp / Elixir

## Bower
Due to Gulp's asynchronous nature, if you try to have Bower run as part of your Gulp workflow, then there's a good chance that Bower won't have pulled in all of your dependencies before Gulp starts trying to concat/minify them. As such, you'll usually hit an error like "could not find file""doesn't exist" or some such.

In vanilla Gulp, this can be helped with some plugins which allow forcing synchronicity upon specific tasks or even perhaps with simple callbacks, but in Elixir there doesn't currently appear to be any real solution.

Instead, for my Laravel/Lumen projects I've just been running `gulp bower && gulp[ --production]` to ensure that the dependencies are successfully fetched prior to anything trying to work with them.
