# vi: set ft=ruby
forge 'https://forgeapi.puppetlabs.com'

# This file manages Puppet module dependencies.
#
# It works a lot like Bundler. We provide some core modules by
# default. This ensures at least the ability to construct a basic
# environment.

# Shortcut for a module from GitHub's boxen organization
def github(name, *args)
  options ||= if args.last.is_a? Hash
    args.last
  else
    {}
  end

  if path = options.delete(:path)
    mod name, :path => path
  else
    version = args.first
    options[:repo] ||= "boxen/puppet-#{name}"
    mod name, version, :github_tarball => options[:repo]
  end
end

# Shortcut for a module under development
def dev(name, *args)
  mod "puppet-#{name}", :path => "#{ENV['HOME']}/src/boxen/puppet-#{name}"
end

# Includes many of our custom types and providers, as well as global
# config. Required.

github "boxen", "3.10.1"

# Support for default hiera data in modules

github "module_data", "0.0.3", :repo => "ripienaar/puppet-module-data"

# Core modules for a basic development environment. You can replace
# some/most of these if you want, but it's not recommended.

# Windows support
mod 'puppetlabs/inifile', '1.1.1'
mod 'puppetlabs/reboot', '0.1.9'
mod 'puppetlabs/registry', '1.0.3'
mod 'puppetlabs/powershell', '1.0.4'
mod 'puppetlabs-win_desktop_shortcut', '0.0.4'
mod 'rismoney/chocolatey', '0.4.0'
mod 'opentable/download_file', '1.1.0'

# Optional/custom modules. There are tons available at
# https://github.com/boxen.
