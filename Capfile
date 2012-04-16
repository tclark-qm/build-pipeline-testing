gem 'qmg-release', '1.0.1'
require 'qmg-release'

default_run_options[:pty] = true
module_names = %w(pipeline-app)
uat_servers = ["ec2-46-51-148-94.eu-west-1.compute.amazonaws.com"]
prod_servers = ["ec2-176-34-73-181.eu-west-1.compute.amazonaws.com"]

####################
# Local Deployment #
####################

namespace :local do
	local = LocalDeploy.new(self, module_names)

	desc "Deploy application locally"
	task :deploy do
		local.deploy
	end

	desc "Start tomcat"
	task :"tomcat-start" do
		local.start_tomcat
	end

	desc "Stop tomcat"
	task :"tomcat-stop" do
		local.stop_tomcat
	end
end


####################
# UAT Deployment   #
####################

namespace :uat do
	remote = RemoteDeploy.new(self, module_names, uat_servers)

	task :deploy do
		remote.deploy build_number
	end
end


####################
# PROD Deployment  #
####################

namespace :prod do
	remote = RemoteDeploy.new(self, module_names, prod_servers)

	task :deploy do
		remote.deploy build_number
	end
end
