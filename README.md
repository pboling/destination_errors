# DestinationErrors

Allows you to create a class that has multiple error surfaces registered but stays within the familiar territory of `ActiveRecord::Validations`.

| Project                 |  DestinationErrors    |
|------------------------ | ----------------- |
| gem name                |  destination_errors   |
| license                 |  MIT              |
| expert support          |  [![Get help on Codementor](https://cdn.codementor.io/badges/get_help_github.svg)](https://www.codementor.io/peterboling?utm_source=github&utm_medium=button&utm_term=peterboling&utm_campaign=github) |
| download rank               |  [![Total Downloads](https://img.shields.io/gem/rt/destination_errors.svg)](https://rubygems.org/gems/destination_errors) |
| version                 |  [![Gem Version](https://badge.fury.io/rb/destination_errors.png)](http://badge.fury.io/rb/destination_errors) |
| dependencies            |  [![Dependency Status](https://gemnasium.com/pboling/destination_errors.png)](https://gemnasium.com/pboling/destination_errors) |
| code quality            |  [![Code Climate](https://codeclimate.com/github/pboling/destination_errors.png)](https://codeclimate.com/github/pboling/destination_errors) |
| inline documenation     |  [![Inline docs](http://inch-ci.org/github/pboling/destination_errors.png)](http://inch-ci.org/github/pboling/destination_errors) |
| continuous integration  |  [![Build Status](https://secure.travis-ci.org/pboling/destination_errors.png?branch=master)](https://travis-ci.org/pboling/destination_errors) |
| test coverage           |  [![Coverage Status](https://coveralls.io/repos/pboling/destination_errors/badge.png)](https://coveralls.io/r/pboling/destination_errors) |
| homepage                |  [on Github.com][homepage] |
| documentation           |  [on Rdoc.info][documentation] |
| live chat               |  [![Join the chat at https://gitter.im/pboling/destination_errors](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/pboling/destination_errors?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) |
| Spread ~♡ⓛⓞⓥⓔ♡~      |  [on Coderbits][coderbits], [on Coderwall][coderwall] |

[semver]: http://semver.org/
[pvc]: http://docs.rubygems.org/read/chapter/16#page74
[railsbling]: http://www.railsbling.com
[peterboling]: http://www.peterboling.com
[coderbits]: https://coderbits.com/pboling
[coderwall]: http://coderwall.com/pboling
[documentation]: http://rdoc.info/github/pboling/destination_errors/frames
[homepage]: https://github.com/pboling/destination_errors


## Installation

Add this line to your application's Gemfile:

```ruby
gem 'destination_errors'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install destination_errors

## Usage

Here is a contrived example.

You have three models, and a form that interacts with all of them:
```
class User
  has_one :profile
  has_one :account
end

class Profile
  belongs_to :user
end

class Account
  belongs_to :user
end
```

So you create an admin user form presenter class to handle everything, and you want it to be *railsy*.
```
class AdminUserFormPresenter

  include DestinationErrors

  attr_accessor :user, :profile, :account
  has_error_surfaces [nil, :user, :profile, :account]

  def initialize(*args)
    @surface_errors_on = nil # nil means errors will be moved onto this instance.
  end

end
```

For more example usage see the specs.


## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`.

## Maintenance

To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release` to create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Versioning

This library aims to adhere to [Semantic Versioning 2.0.0](http://semver.org/).
Violations of this scheme should be reported as bugs. Specifically,
if a minor or patch version is released that breaks backward
compatibility, a new version should be immediately released that
restores compatibility. Breaking changes to the public API will
only be introduced with new major versions.

As a result of this policy, you can (and should) specify a
dependency on this gem using the [Pessimistic Version Constraint](http://docs.rubygems.org/read/chapter/16#page74) with two digits of precision.

For example:

    spec.add_dependency 'destination_errors', '~> 0.0'

## Contributing

1. Fork it ( https://github.com/[my-github-username]/destination_errors/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Make sure to add tests!
6. Create a new Pull Request

## Contributors

See the [Network View](https://github.com/trumaker/destination_errors/network)

