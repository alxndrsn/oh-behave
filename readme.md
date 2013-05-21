Oh, Behave!
===========

Groovy BDD toolkit for [Grails][1] and [Spock][2].

# The Scripts

Currently this toolkit consists of some simple scripts for converting lists of functionality in markdown style into Spock tests, e.g.:

	# MyDomainClass

	* instance should have a name
	* saving without a description should fail validation
	* doMagic should cause rabbit to appear

when passed to `spocify` should generate the following test class:

	class MyDomainClassSpec extends Specification {
		def 'instance should have a name'() { expect: TODO() }
		def 'saving without a description should fail validation'() { expect: TODO() }
		def 'doMagic should cause rabbit to appear'() { expect: TODO() }

		private void TODO(message='Not yet implemented.') { throw new RuntimeException("TODO: ${message}") }
	}

To reverse the process, use the `report` script

## Spocify

This will turn a markdown file containing descriptions of behaviour into outline Grails Spock unit tests.

## Report

This will turn spock tests into a markdown file describing the behaviour that is being tested.

[1]: http://www.grails.org
[2]: https://code.google.com/p/spock/

