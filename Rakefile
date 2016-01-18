require 'pathname'
require 'erb'

require 'dotenv'
Dotenv.load

ROOT_PATH = Pathname(__FILE__).parent

desc 'generates Ghost configuration file from .env file'
task :config do
  template = File.read(ROOT_PATH.join('config.js.erb'))
  File.write(ROOT_PATH.join('Ghost', 'config.js'), ERB.new(template).result)
end

desc 'builds and minifies assets for production'
task :build do
  cd 'Ghost'
  sh 'sudo npm install -g grunt-cli'
  sh 'npm install'
  sh 'grunt init'
  sh 'grunt prod'
end
