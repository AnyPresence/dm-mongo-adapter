require 'rubygems'
require 'rake'
require 'rake/clean'

CLOBBER.include ['pkg', '*.gem', 'doc', 'coverage', 'measurements']

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name      = 'dm-mongo-adapter'
    gem.summary   = 'MongoDB DataMapper Adapter'
    gem.email     = "piotr.solnica@gmail.com"
    gem.homepage  = "http://github.com/solnic/dm-mongo-adapter"
    gem.authors   = ['Piotr Solnica']
    gem.has_rdoc  = false

    # Exclude files
    gem.files.exclude "bin/console"
  end
  Jeweler::GemcutterTasks.new
  FileList['tasks/**/*.rake'].each { |task| import task }
rescue LoadError
  puts 'Jeweler (or a dependency) not available. Install it with: sudo gem ' \
       'install jeweler'
end

task :install_fast do
  sh "rake build; gem install pkg/dm-mongo-adapter*.gem --local"
end
