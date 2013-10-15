require 'pathname'

source 'http://rubygems.org'

gemspec

SOURCE        = ENV.fetch('SOURCE', :git).to_sym
REPO_POSTFIX  = SOURCE == :path ? ''                                : '.git'
DATAMAPPER    = SOURCE == :path ? Pathname(__FILE__).dirname.parent : 'http://github.com/datamapper'
DM_VERSION    = '~> 1.2.0.rc2'
MONGO_VERSION = '~> 1.4.0'

group :runtime do

  # MongoDB driver
  gem 'bson_ext', MONGO_VERSION, :platforms => [ :mri ]
  gem 'mongo',    MONGO_VERSION
  gem 'dm-core', DM_VERSION, SOURCE => "#{DATAMAPPER}/dm-core#{REPO_POSTFIX}", :tag => 'v1.2.0'

  plugins = ENV['PLUGINS'] || ENV['PLUGIN']
  plugins = plugins.to_s.tr(',', ' ').split.push('dm-migrations').push('dm-aggregates').uniq

  plugins.each do |plugin|
    gem plugin, DM_VERSION, SOURCE => "#{DATAMAPPER}/#{plugin}#{REPO_POSTFIX}", :tag => 'v1.2.0'
  end
end

group :development do
  gem 'dm-annoing-modificators', :git => 'git://github.com/AnyPresence/dm-annoing-modificators'
end

platforms :mri_18 do
  group :quality do
    gem 'rcov',      '~> 0.9.9'
    gem 'yard',      '~> 0.6'
    gem 'yardstick', '~> 0.2'
  end
end
