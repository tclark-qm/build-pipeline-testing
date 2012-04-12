gem 'qmg-release', '1.0.1'
require 'qmg-release'

default_run_options[:pty] = true

namespace :local do
	local = LocalDeploy.new(self, "pipeline-app")

	desc "deploy test application to localhost"
	task :deploy do
		local.deploy
	end
end
