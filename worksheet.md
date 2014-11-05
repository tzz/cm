Configuration Management BINGO

Try these out for yourself on the lab systems.  Setting up any of these tools takes 5 minutes or less, and you can easily find online resources for getting started beyond that.

Explore!  Play!  Have fun!

| BINGO  | Ansible | CFEngine | Chef | Puppet | SaltStack |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| Make file from template  | ☐ | ☐ | ☐ | ☐ | ☐ |
| Remove file  | ☐ | ☐ | ☐ | ☐ | ☐ |
| Install/update package  | ☐ | ☐ | ☐ | ☐ | ☐ |
| Add user  | ☐ | ☐ | ☐ | ☐ | ☐ |
| Had beer with developer  | ☐ | ☐ | ☐ | ☐ | ☐ |
| Been to a BoF session / conference  | ☐ | ☐ | ☐ | ☐ | ☐ |

<hr>

Answer key:

Versions:

* Ansible: 1.7
* CFEngine: 3.6
* Chef: 11
* Puppet: 3.7
* SaltStack: 2014.1.13

| BINGO  | Ansible | CFEngine | Chef | Puppet | SaltStack |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| Make file from template  | <pre>template:<br>  src: /path/template.file<br>  dest: /my/file</pre> | `file_make` `file_mustache` `edit_line` | <pre>template "/my/file" do<br>  source "template.file"<br>end</pre> | <pre>file { "my_thing":<br>  path => "/my/file",<br>  content => template('module/template.file'),<br>  }</pre> | <pre>/my/file:<br>  file.managed:<br>  - source: salt://module/template.file</pre> |
| Remove file/dir  | <pre>file:<br>  path: /my/dir-or-file<br>  state: absent</pre> | `file_tidy` `rm_rf` | <pre>file "/my/file" do<br>  action :delete<br>end</pre> <pre>directory "/my/path" do<br>  recursive true<br>  action :delete<br>end</pre> | <pre>file {'remove_things':<br>  ensure => absent,<br>  path => '/my/fileordir',<br>  recurse => true,<br>  purge => true,<br>  force => true,<br>  }</pre> | <pre>/my/path:<br>  file.absent:</pre> |
| Install/update package  | <pre>apt: name=vim state=present</pre> <pre>yum: name=vim state=latest</pre> | `package_present` `package_latest` | <pre>package "vim" do<br>  action :install<br>end</pre> <pre>package "vim" do<br>  action :upgrade<br>end</pre> | <pre>package { "vim":<br>ensure => "installed";<br>}</pre> <pre>package { "vim":<br>ensure => "latest";<br>}</pre> | <pre>vim:<br>  pkg.installed</pre> <pre>vim:<br>  pkg.latest</pre> |
| Add user  | `user: name=tzz` | <pre>users:<br> "tzz"<br>  policy => "present";<pre> | <pre>user "tzz" do<br>...<br>end</pre> | <pre>user { "tzz":<br>ensure => present;<br>}<pre> | <pre>tzz:<br>  user.present:</pre> |
| Had beer with developer  | ☐ | ☐ | ☐ | ☐ | ☐ |
| Been to a BoF session / conference  | ☐ | ☐ | ☐ | ☐ | ☐ |
