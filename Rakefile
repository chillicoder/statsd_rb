# encoding: utf-8

require 'rubygems'
require 'bundler'
begin
  Bundler.setup(:default, :development)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts "Run `bundle install` to install missing gems"
  exit e.status_code
end
require 'rake'

require 'jeweler'
require './lib/statsd/version.rb'
Jeweler::Tasks.new do |gem|
  # gem is a Gem::Specification... see http://docs.rubygems.org/read/chapter/20 for more options
  gem.name = "statsd"
  gem.version = Statsd::Version::STRING
  gem.homepage = "http://github.com/seatgeek/statsd_rb"
  gem.license = "MIT"
  gem.summary = %Q{A network daemon for aggregating statistics (counters and timers), rolling them up, then sending them to graphite.}
  gem.description = File.read('README.md')
  gem.email = "michael.dauria@gmail.com"
  gem.authors = ["Michael D'Auria"]
  # dependencies defined in Gemfile
end
Jeweler::RubygemsDotOrgTasks.new

require 'rspec/core'
require 'rspec/core/rake_task'
RSpec::Core::RakeTask.new(:spec) do |spec|
  spec.pattern = FileList['spec/**/*_spec.rb']
end

RSpec::Core::RakeTask.new(:rcov) do |spec|
  spec.pattern = 'spec/**/*_spec.rb'
  spec.rcov = true
end

task :default => :spec

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  version = Statsd::Version::STRING

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "statsd #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end