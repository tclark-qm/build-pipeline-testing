gem 'qmg-release', '1.0.1'
require 'qmg-release'

default_run_options[:pty] = true
module_names = %w(pipeline-app)

####################
# Local Deployment #
####################

namespace :local do
	local = LocalDeploy.new(self, app_name)

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

uat_servers = ["ec2-176-34-69-217.eu-west-1.compute.amazonaws.com"]

namespace :uat do
	remote = RemoteDeploy.new(self, module_names, uat_servers)

	task :deploy do
		remote.deploy build_number
	end
end


####################
# PROD Deployment  #
####################

prod_servers = ["ec2-79-125-49-224.eu-west-1.compute.amazonaws.com"]

namespace :prod do
	remote = RemoteDeploy.new(self, app_name, prod_servers)

	task :deploy do
		remote.deploy build_number
	end
end
