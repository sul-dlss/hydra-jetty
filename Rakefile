require 'pathname'
require 'fileutils'

ROOT = File.expand_path(File.dirname(__FILE__))
DIST_DIR = 'dist'
ORIG_WARFILE = 'fcrepo-webapp-4.0.0-beta-04-SNAPSHOT.war'

desc "Copy fedora war file to dist directory, renamed with VERSION"
task :copy_war_to_dist do
  root = Pathname.new ROOT
  dist = root.join DIST_DIR
  dist.mkdir unless dist.exist?

  version = IO.read(root.join('VERSION')).strip
  FileUtils.cp(root.join('webapps', ORIG_WARFILE), dist.join("fedora4-#{version}.war"))
end

task :default => :copy_war_to_dist
