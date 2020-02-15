# Ansible Role: Apt-Cacher NG
[![Build Status](https://travis-ci.org/pvelati/ansible-role-apt-cacher-ng.svg?branch=master)](https://travis-ci.org/pvelati/ansible-role-apt-cacher-ng) [![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fpvelati%2Fansible-role-apt-cacher-ng.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fpvelati%2Fansible-role-apt-cacher-ng?ref=badge_shield)

This role installs and configures [apt-cacher-ng] on Debian servers.

## Requirements
OS: Debian

## Role Variables
```
apt_cacher_ng:
  port: "3142"
  report_page: "acng-report.html"
  cache_dir: "/srv/apt-cacher-ng"
  log_dir: "/var/log/apt-cacher-ng"
  verbose_log: "0"
  local_dirs: "acng-doc /usr/share/doc/apt-cacher-ng"
  support_dir: "/usr/lib/apt-cacher-ng"
  pid_file: "/var/run/apt-cacher-ng/pid"
  ex_treshold: "8"
  remap_debrep: "file:deb_mirror*.gz /debian ; file:backends_debian"
  remap_uburep: "file:ubuntu_mirrors /ubuntu ; file:backends_ubuntu"
  remap_debvol: "file:debvol_mirror*.gz /debian-volatile ; file:backends_debvol"
  remap_alxrep: "file:archlx_mirrors /archlinux ; file:backend_archlx"
  remap_fedora: "file:fedora_mirrors"
  remap_epel: "file:epel_mirrors"
  remap_slrep: "file:sl_mirrors"
  remap_gentoo: "file:gentoo_mirrors.gz /gentoo ; file:backends_gentoo"
  remap_centosmirrorlist: "mirrorlist.centos.org"
  remap_centos: "file:centos_mirrors"
  remap_alpine: "dl-cdn.alpinelinux.org"
  request_appendix: "X-Tracking-Choice: do-not-track\r\n"
  dont_cache: "mirrorlist.centos.org"
  vfile_pattern_ex: '(metalink\?repo=[0-9a-zA-Z-]+&arch=[0-9a-zA-Z_-]+|/\?release=[0-9]+&arch=|repodata/.*\.(xml|sqlite)\.(gz|bz2)|APKINDEX.tar.gz|filelists\.xml\.gz|filelists\.sqlite\.bz2|repomd\.xml|packages\.[a-zA-Z][a-zA-Z]\.gz)'
  pfile_pattern_ex: '(/dists/.*/by-hash/.*|\.tgz|\.tar|\.xz|\.bz2|\.rpm|\.apk)$"'
  max_con_threads: 120
  admin_name: "admin"
  admin_password: "admin"
  passthrough_pattern: "^(.*):443$"
```

## Dependencies

None

## Example Playbook
```
---
- hosts: apt-cacher-server
  become: true
  roles:
    - role: ansible-role-apt-cacher-ng
```

## License

MIT

[apt-cacher-ng]: <https://www.unix-ag.uni-kl.de/~bloch/acng/>
