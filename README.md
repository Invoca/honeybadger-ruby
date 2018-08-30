# Honeybadger for Ruby

[![Build Status](https://secure.travis-ci.org/honeybadger-io/honeybadger-ruby.png?branch=master)](http://travis-ci.org/honeybadger-io/honeybadger-ruby)
[![Gem Version](https://badge.fury.io/rb/honeybadger.png)](http://badge.fury.io/rb/honeybadger)

This is the notifier gem for integrating apps with the :zap: [Honeybadger Exception Notifier for Ruby and Rails](http://honeybadger.io).

When an uncaught exception occurs, Honeybadger will POST the relevant data to the Honeybadger server specified in your environment.

## Documentation and Support

For comprehensive documentation and support, [check out our documentation site](https://docs.honeybadger.io/ruby/index.html).

### `Honeybadger.local_variable_filter()`: Programmatically filter local variable data
 This method lets you add a callback that will be run for each local variable that is about to be reported to Honeybadger. The value returned by your callback will be logged with the exception.
 #### Use this method if:
 * You need to filter local variables that meet complex criteria
* The built-in configuration options for filter keys aren't enough
* You want to augment the local variable data
 #### Examples:
 ```ruby
# Redacting a local variable because it contains a password attribute
Honeybadger.local_variable_filter do |symbol, object, filter_keys|
  if object.is_a?(MyPoro)
    object.inspect unless object.inspect ~= /password/
  else
    value
  end
end
```

## Changelog

See https://github.com/honeybadger-io/honeybadger-ruby/blob/master/CHANGELOG.md

## Development

Pull requests are welcome. If you're adding a new feature, please [submit an issue](https://github.com/honeybadger-io/honeybadger-ruby/issues/new) as a preliminary step; that way you can be (moderately) sure that your pull request will be accepted.

If you're integrating your gem/open source project with Honeybadger, please consider submitting an official plugin to our gem. [Submit an issue](https://github.com/honeybadger-io/honeybadger-ruby/issues/new) to discuss with us!

We use [YARD](https://yardoc.org/) to document our API. Classes and methods which are safe to depend on in your gems/projects are marked "Public". All other classes/methods are considered internal and may change without notice -- don't depend on them! If you need a new public API, we're happy to work with you. [Submit an issue](https://github.com/honeybadger-io/honeybadger-ruby/issues/new) to discuss.

### To contribute your code:

1. Fork it.
2. Create a topic branch `git checkout -b my_branch`
3. Make your changes and add an entry to the [CHANGELOG](CHANGELOG.md).
4. Commit your changes `git commit -am "Boom"`
5. Push to your branch `git push origin my_branch`
6. Send a [pull request](https://github.com/honeybadger-io/honeybadger-ruby/pulls)

### Running the tests

We're using the [Appraisal](https://github.com/thoughtbot/appraisal) gem to run
our [RSpec](https://www.relishapp.com/rspec/) test suite against multiple
versions of [Rails](http://rubyonrails.org/).

* The unit test suite can be run with `rake spec:units`.
* The integration test suite can be run with `rake spec:features`.
* The combined suite can be run with `rake`.

### License

The Honeybadger gem is MIT licensed. See the [LICENSE](https://raw.github.com/honeybadger-io/honeybadger-ruby/master/LICENSE) file in this repository for details.
