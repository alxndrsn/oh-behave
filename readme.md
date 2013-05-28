Oh, Behave!
===========

Groovy BDD toolkit for [Grails][1] and [Spock][2].

# The Scripts

Currently this toolkit consists of some simple scripts for converting lists of functionality in markdown style into Spock tests, e.g.:

	# MyDomainClass

	* instance should have a name
	* saving without a description should fail validation
	* doMagic should cause rabbit to appear


	# MyServiceClass
	etc.

When passed to `spocify` this will generate a test class containing stubbed test methods for each top-level section.  All tests will fail until the implementation is added.

For `MyDomainClass` above, the generated spec file will look like:

	class MyDomainClassSpec extends Specification {
		def 'instance should have a name'() { expect: TODO() }
		def 'saving without a description should fail validation'() { expect: TODO() }
		def 'doMagic should cause rabbit to appear'() { expect: TODO() }

		private void TODO(message='Not yet implemented.') { throw new RuntimeException("TODO: ${message}") }
	}

To reverse the process, use the `exposition` script

## spocify

This will turn a markdown file containing descriptions of behaviour into outline Grails Spock unit tests.

## exposition

This will turn spock tests into a markdown file describing the behaviour that is being tested.

[1]: http://www.grails.org
[2]: https://code.google.com/p/spock/

# TODO

## `given`, `when`, `then`; `expect` steps

Proposed new format for desciption files:

	# first class name

	## first assertion about behaviour
	1. given some predicate
	2. when some action is taken
	3. then some assertion can be made

	## second assertaion about behaviour
	1. given some predicate
	2. expect some truth


	# second class name

	## etc.

This would then generate spock specs with `given:`, `when:`, `then:` labels inserted, such as:

	def 'first assertion about behaviour'() {
		given: 'some predicate':
			TODO('not implemented: some predicate')
		when: 'some action is taken'
			TODO('not implemented: some action is taken')
		then: 'some assertion can be made'
			TODO('not implemented: some assertion can be made')
	}
	...

It should be simple to allow either format to be used, and use the simplest possible when generating behaviour reports.

