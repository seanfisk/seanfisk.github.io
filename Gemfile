# -*- mode: ruby; coding: utf-8; -*-

source 'https://rubygems.org'

# Use the same versions as GitHub pages
# https://jekyllrb.com/docs/github-pages/#deploying-jekyll-to-github-pages
require 'json'
require 'open-uri'
versions = JSON.parse(open('https://pages.github.com/versions.json').read)
gem 'github-pages', versions['github-pages']

gem 'octopress', '~> 3.0'
