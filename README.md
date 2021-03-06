# aws_firewall

[![Puppet Forge](http://img.shields.io/puppetforge/v/pmuller/aws_firewall.svg)](https://forge.puppetlabs.com/pmuller/aws_firewall)
[![Puppet Forge downloads](https://img.shields.io/puppetforge/dt/pmuller/aws_firewall.svg)](https://forge.puppetlabs.com/pmuller/aws_firewall)
[![Build Status](https://travis-ci.org/pmuller/puppet-aws_firewall.png)](https://travis-ci.org/pmuller/puppet-aws_firewall)

#### Table of Contents

1. [Description](#description)
2. [Usage - Configuration options and additional functionality](#usage)
3. [Reference - An under-the-hood peek at what the module is doing and how](#reference)
4. [Limitations - OS compatibility, etc.](#limitations)
5. [Development - Guide for contributing to the module](#development)
6. [Changelog](#changelog)

## Description

This module generates granular iptables rules to restrict access to Amazon Web Services.

## Usage

### Create an ipset that contains specific AWS IP prefixes

```puppet
aws_firewall::ipset { 'ap-south-1-s3':
  regions  => ['ap-south-1'],
  services => ['S3'],
}
```

### Create an ipset-based iptables rule

```puppet
aws_firewall::rule::ipset { '200 Allow access to S3 in us-east-1':
  ipset => 'ap-south-1-s3',
}
```

### Create an iptables rule to allow access to EC2 metadata
```puppet
aws_firewall::rule::metadata { '200 Allow access to EC2 instance metadata':
  uid => 'someone',
}
```

## Reference

See [reference](https://github.com/pmuller/puppet-aws_firewall/blob/master/doc/reference.md)

## Limitations

* Only tested on RedHat-like Linux distributions
* IPv6 prefixes are not yet supported

## Development

See [development](https://github.com/pmuller/puppet-aws_firewall/blob/master/doc/development.md)

## Changelog

See [CHANGELOG](https://github.com/pmuller/puppet-aws_firewall/blob/master/CHANGELOG.md)
