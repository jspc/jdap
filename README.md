# jspc's directory access ~~protocol~~ program

A go package providing ldap operations, including simple implementations.

This project originally started as a [github.com/glauth/glauth](github.com/glauth/glauth), with some slightly different goals to the original, but the fork was abandoned:

1. The original has a really tediously complex, totally idiomatic build process with lots of make targets. And also all of the make targets should either be `.PHONY`, or point to the files they create. It's just awful
1. The original has no tests. Like, none. I know there's a file called `glauth_test.go` in the original but... no.
1. The package structure is over complicated with no apparent benefit. What am I supposed to do with this?
1. We want to allow different backends for config, using the power of interfaces
1. We want to defer as much as possible, like frontends, and tls to smarter tools (there are many awesome frontends/tools, and nginx can from ldap quite easily)
1. glauth doesn't really do anything we need specifically; we're ultimately wrapping `github.com/vjeantet/ldapserver` anyway, so why bother hacking on other code?

To this end we will:

1. Provide a package containing library code for handling ldap operations
1. Provide a series of implementations of a glauth backend (as a reference, and for end users)
1. Provide some simple binaries showing different backends, both as a quickstart and to show developers how to build their own systems

## Project goals

 - [ ] To provide a docker container showing jdap backed with static, user credentials
 - [ ] To provide a docker container showing jdap backed with a standard unix `passwd` authenticator
