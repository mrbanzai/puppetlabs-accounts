#This file is generated by ModuleSync, do not edit.

source ENV['GEM_SOURCE'] || "https://rubygems.org"

# Determines what type of gem is requested based on place_or_version.
def gem_type(place_or_version)
  if place_or_version =~ /^git:/
    :git
  elsif place_or_version =~ /^file:/
    :file
  else
    :gem
  end
end

# Find a location or specific version for a gem. place_or_version can be a
# version, which is most often used. It can also be git, which is specified as
# `git://somewhere.git#branch`. You can also use a file source location, which
# is specified as `file://some/location/on/disk`.
def location_for(place_or_version, fake_version = nil)
  if place_or_version =~ /^(git[:@][^#]*)#(.*)/
    [fake_version, { :git => $1, :branch => $2, :require => false }].compact
  elsif place_or_version =~ /^file:\/\/(.*)/
    ['>= 0', { :path => File.expand_path($1), :require => false }]
  else
    [place_or_version, { :require => false }]
  end
end



group :development, :unit_tests do
  gem 'metadata-json-lint',                   :require => false
  gem 'puppet_facts',                         :require => false
  gem 'puppet-blacksmith', '>= 3.4.0',      :require => false
  gem 'puppetlabs_spec_helper', '>= 1.2.1', :require => false
  gem 'rspec-puppet', '>= 2.3.2',           :require => false
  gem 'rspec-puppet-facts',                   :require => false
  gem 'simplecov',                            :require => false
  gem 'parallel_tests',                       :require => false
  gem 'rubocop', '0.41.2',                  :require => false if RUBY_VERSION < '2.0.0'
  gem 'rubocop',                              :require => false if RUBY_VERSION >= '2.0.0'
  gem 'rubocop-rspec', '~> 1.6',            :require => false if RUBY_VERSION >= '2.3.0'
  gem 'json_pure', '<= 2.0.1',              :require => false if RUBY_VERSION < '2.0.0'
end

group :system_tests do
  gem 'beaker', *location_for(ENV['BEAKER_VERSION'])                             if RUBY_VERSION >= '2.3.0'
  gem 'beaker', *location_for(ENV['BEAKER_VERSION' || '< 3'])                    if RUBY_VERSION < '2.3.0'
  gem 'beaker-rspec', *location_for(ENV['BEAKER_RSPEC_VERSION' || '>= 3.4'])    
  gem 'serverspec',                                                                 :require => false
  gem 'beaker-puppet_install_helper',                                               :require => false
  gem 'master_manipulator',                                                         :require => false
  gem 'beaker-hostgenerator', *location_for(ENV['BEAKER_HOSTGENERATOR_VERSION'])
end

gem 'facter', *location_for(ENV['FACTER_GEM_VERSION'])
gem 'puppet', *location_for(ENV['PUPPET_GEM_VERSION'])


# Evaluate Gemfile.local if it exists
if File.exists? "#{__FILE__}.local"
  eval(File.read("#{__FILE__}.local"), binding)
end

# Evaluate ~/.gemfile if it exists
if File.exists?(File.join(Dir.home, '.gemfile'))
  eval(File.read(File.join(Dir.home, '.gemfile')), binding)
end
# vim:ft=ruby
