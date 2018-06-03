$LOAD_PATH.unshift 'lib'

module FuryiousTask
  FURYIOUS_NAME = 'furyious'
  FURYIOUS_VERSION = '0.1.0'
  FURYIOUS_ARCHITECTURE = 'all'
  FURYIOUS_MAINTAINER = 'hi@markjeee.com'

  def self.package_name
    FURYIOUS_NAME
  end

  def self.version
    FURYIOUS_VERSION
  end

  def self.architecture
    FURYIOUS_ARCHITECTURE
  end

  def self.maintainer
    FURYIOUS_MAINTAINER
  end

  def self.deb_package_file
    '%s_%s_%s.deb' % [ package_name, version, architecture ]
  end

  def self.rpm_package_file
    '%s_%s_%s.rpm' % [ package_name, version, architecture ]
  end

  def self.source_files
    files = {
      'bin/furyious' => '/usr/bin/furyious'
    }

    files
  end

  def self.source_files_map
    source_files.inject('') do |s, (k,v)|
      s += '%s=%s' % [ k, v ]; s
    end
  end
end

desc 'Create Debian package'
task :create_deb do
  puts 'Creating deb...'

  cmd = 'bundle exec fpm -f -s dir -t deb -a %s -m %s -n %s -v %s -p %s %s' %
        [ FuryiousTask.architecture,
          FuryiousTask.maintainer,
          FuryiousTask.package_name,
          FuryiousTask.version,
          FuryiousTask.deb_package_file,
          FuryiousTask.source_files_map ]

  puts 'CMD: %s' % cmd
  system(cmd)

  puts 'Done creating deb'
end

desc 'Push Debian package to Gemfury'
task :push_deb do
  cmd = 'bundle exec fury push %s' % FuryiousTask.deb_package_file
  system(cmd)
end

desc 'Create RPM package'
task :create_rpm do
  puts 'Creating rpm...'

  cmd = 'bundle exec fpm -f -s dir -t rpm --rpm-os linux -a %s -m %s -n %s -v %s -p %s %s' %
        [ FuryiousTask.architecture,
          FuryiousTask.maintainer,
          FuryiousTask.package_name,
          FuryiousTask.version,
          FuryiousTask.rpm_package_file,
          FuryiousTask.source_files_map ]

  puts 'CMD: %s' % cmd
  system(cmd)

  puts 'Done creating rpm'
end

desc 'Push Debian package to Gemfury'
task :push_rpm do
  cmd = 'bundle exec fury push %s' % FuryiousTask.rpm_package_file
  system(cmd)
end

task :default => [ :create_deb, :create_rpm ]
