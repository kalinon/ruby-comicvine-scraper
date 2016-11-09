require 'bundler/gem_tasks'
require 'rake/testtask'
require 'yard'

# Test tasks
Rake::TestTask.new(:test) do |t|
  t.libs << 'test'
  t.libs << 'lib'
  t.test_files = FileList['test/**/*_test.rb']
end

YARD::Rake::YardocTask.new do |t|
  t.files   = ['lib/**/*.rb'] # optional
  t.options = %w{--private} # optional
  t.stats_options = ['--list-undoc'] # optional
end

# Default task
task :default => :test

task :gen_checksum do
  require 'digest/sha2'
  built_gem_path = 'pkg/comicvine-scraper-'+ComicVine::Scraper::VERSION+'.gem'
  checksum = Digest::SHA256.new.hexdigest(File.read(built_gem_path))
  checksum_path = 'checksum/comicvine-scraper-'+ComicVine::Scraper::VERSION+'.gem.sha256'
  File.open(checksum_path, 'w' ) {|f| f.write(checksum) }
end