# TLD Notes
Just a quick collection of resources/information that I've come across that answer some general questions that I've had difficulty finding details for in the past.

## gTLDs
### Reserved
> These are *great* for TESTING or LOCAL DEV SERVERS, such as Vagrant boxes.

In accordance with [RFC-2606 ("Reserved Top Level DNS Names")](http://www.ietf.org/rfc/rfc2606.txt), the IETF has permanently reserved a small handful of gTLDs for the purpose of testing, documentation, and what I'll just call "implicit loopbacks" where (ideally) the request resolves back to the originator's machine. They are as follows:

- `.test`
	- ".test" is recommended for use in testing of current or new DNS related code.
- `.example`
	- ".example" is recommended for use in documentation or as examples.
- `.invalid`
	- ".invalid" is intended for use in online construction of domain names that are sure to be invalid and which it is obvious at a glance are invalid.
- `.localhost`
	- The ".localhost" TLD has traditionally been statically defined in host DNS implementations as having an A record pointing to the loop back IP address and is reserved for such use. Any other use would conflict with widely deployed code which assumes this use.

As the above (official) explanations are somewhat vague, a read of [RFC-6761 ("Special-Use Domain Names")](https://tools.ietf.org/html/rfc6761) may be worthwhile, which outlines the intended use case(s) of each one.

#### .local
Desrerving of its own section, it is an especially terrible idea to use the `.local` gTLD for dev/test/etc. boxes, yet despite this it continues to be incredibly common among veteran network/system admins and any juniors trained by them due to the fact that there *was* a period of time in which this was actually *suggested*.

The short version is that it is given special meaning by some versions of some Operating Systems when used in certain types of network configurations (not very helpful, I know). The most common scenario in which this is problematic pertains to the way that Apple systems tend to "automagically" handle domain/machine names ending in this gTLD. This is more fully documented in the mDNS guidelines in [RFC-6762 ("Multicast DNS")](https://tools.ietf.org/html/rfc6762#page-5) on page 5.


## "Second Level" Domain Names
In addition to the reserved gTLDs, the IETF has also permanently reserved the following domain names (which is also documented in [RFC-2606 ("Reserved Top Level DNS Names")](http://www.ietf.org/rfc/rfc2606.txt)):

- example.com
- example.net
- example.org

## Other
- Not strictly related to TLDs but rather the Internet as a whole is the venerable [Hobbes' Internet Timeline](http://www.zakon.org/robert/internet/timeline/).
