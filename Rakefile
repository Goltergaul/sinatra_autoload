require 'rubygems'
require 'rake'
require 'bundler'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "sinatra_autoload"
    gem.summary = %Q{Auto loader for required sinatra files.}
    gem.description = %Q{Do not load files into memory until they are accessed / needed inside your application.}
    gem.email = "justin.smestad@gmail.com"
    gem.homepage = "http://github.com/jsmestad/sinatra_autoload"
    gem.authors = ["Justin Smestad", "Gabe Varela"]

    manifest = Bundler::Environment.load(File.dirname(__FILE__) + '/Gemfile')
    manifest.dependencies.each do |d|
      next if d.only && d.only.include?('test')
      gem.add_dependency(d.name, d.version)
    end

    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: sudo gem install jeweler"
end

require 'spec/rake/spectask'
Spec::Rake::SpecTask.new(:spec) do |spec|
  spec.libs << 'lib' << 'spec'
  spec.spec_files = FileList['spec/**/*_spec.rb']
end

Spec::Rake::SpecTask.new(:rcov) do |spec|
  spec.libs << 'lib' << 'spec'
  spec.pattern = 'spec/**/*_spec.rb'
  spec.rcov = true
end

task :spec => :check_dependencies

task :default => :spec

begin
  require 'yard'
  YARD::Rake::YardocTask.new
rescue LoadError
  task :yardoc do
    abort "YARD is not available. In order to run yardoc, you must: sudo gem install yard"
  end
end
