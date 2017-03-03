source 'https://rubygems.org'

gemspec

version = ENV["RAILS_VERSION"] || "4.2"

if version == 'master'
  gem 'rack', github: 'rack/rack'
  git 'https://github.com/rails/rails.git' do
    gem 'railties'
    gem 'activesupport'
    gem 'activemodel'
    gem 'actionpack'
    # Rails 5
    gem 'actionview'
  end
  # Rails 5
  gem 'rails-controller-testing', github: 'rails/rails-controller-testing'
else
  gem_version = "~> #{version}.0"
  gem 'railties', gem_version
  gem 'activesupport', gem_version
  gem 'activemodel', gem_version
  gem 'actionpack', gem_version
end

if RUBY_VERSION < '2'
  gem 'mime-types', [ '>= 2.6.2', '< 3' ]
end

# https://github.com/bundler/bundler/blob/89a8778c19269561926cea172acdcda241d26d23/lib/bundler/dependency.rb#L30-L54
@windows_platforms = [:mswin, :mingw, :x64_mingw]

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo-data', platforms: (@windows_platforms + [:jruby])

group :bench do
  gem 'benchmark-ips', '>= 2.7.2'
end

group :test do
  gem 'activerecord'
  gem 'sqlite3',                          platform: (@windows_platforms + [:ruby])
  gem 'activerecord-jdbcsqlite3-adapter', platform: :jruby

  gem 'codeclimate-test-reporter', require: false
  gem 'simplecov', '~> 0.10', require: false, group: :development
end

group :development, :test do
  gem 'rubocop', '~> 0.34.0', require: false
end
