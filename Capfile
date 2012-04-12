gem 'qmg-release', '1.0.1'
require 'qmg-release'

default_run_options[:pty] = true

namespace :local do
	desc "deploy test application to localhost"
	task :deploy do
		LocalDeploy.new(self, "build-pipeline-testing").deploy
	end
end
