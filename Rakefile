task default: %w[ubuntu]

CONFIGURATIONS_TAG = 'v1.2.0'

desc 'Build the whole Mezuro packages for Ubuntu'
task :ubuntu => [:mk_structure] do
  sh 'docker build --rm=true --tag mezuro-ubuntu-build -f Dockerfile-ubuntu .'
  sh "docker run -t -i --volume=#{Dir.pwd}/pkgs:/root/mezuro/pkgs mezuro-ubuntu-build"
end

desc 'Create build dirs and fetch source files'
task :mk_structure do
  sh "mkdir -p src"
  sh "git clone https://github.com/mezuro/kalibro_configurations.git -b #{CONFIGURATIONS_TAG} src/kalibro_configurations"
  sh "mkdir -p pkgs"
end

desc 'Undo mk_structure'
task :clean do
  sh "rm -rf src pkgs"
end