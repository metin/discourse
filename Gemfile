source 'https://rubygems.org'
# if there is a super emergency and rubygems is playing up, try
#source 'http://production.cf.rubygems.org'

def rails_master?
  ENV["RAILS_MASTER"] == '1'
end

if rails_master?
  gem 'arel', git: 'https://github.com/rails/arel.git'
  gem 'rails', git: 'https://github.com/rails/rails.git'
  gem 'seed-fu', git: 'https://github.com/SamSaffron/seed-fu.git', branch: 'discourse'
else
  # Rails 5 is going to ship with Action Cable, we have no use for it as
  # we already ship MessageBus, AC introduces dependencies on Event Machine,
  # Celluloid and Faye Web Sockets.
  #
  # Note this means upgrading Rails is more annoying, to do so, comment out the
  # explicit dependencies, and add gem 'rails', bundle update rails and then
  # comment back the explicit dependencies. Leaving this in a comment till we
  # upgrade to Rails 5
  #
  # gem 'activesupport'
  # gem 'actionpack'
  # gem 'activerecord'
  # gem 'actionmailer'
  # gem 'activejob'
  # gem 'railties'
  # gem 'sprockets-rails'
  gem 'rails', '~> 4.2'
  gem 'seed-fu', '~> 2.3.5'
end

gem 'mail'
gem 'mime-types', require: 'mime/types/columnar'

gem 'hiredis'
gem 'redis', require:  ["redis", "redis/connection/hiredis"]
gem 'redis-namespace'

gem 'active_model_serializers', '~> 0.8.3'

gem 'onebox'

gem 'http_accept_language', '~>2.0.5', require: false

gem 'ember-rails', '0.18.5'
gem 'ember-source', '2.10.0'
gem 'ember-handlebars-template', '0.7.5'
gem 'barber'
gem 'babel-transpiler'

gem 'message_bus'

gem 'rails_multisite'

gem 'fast_xs'

gem 'fast_xor'

# while we sort out https://github.com/sdsykes/fastimage/pull/46
gem 'discourse_fastimage', '2.0.3', require: 'fastimage'
gem 'aws-sdk', require: false
gem 'excon', require: false
gem 'unf', require: false

gem 'email_reply_trimmer', '0.1.6'

# note: for image_optim to correctly work you need to follow
# https://github.com/toy/image_optim
# pinned due to https://github.com/toy/image_optim/pull/75, docker image must be upgraded to upgrade
gem 'image_optim', '0.20.2'
gem 'multi_json'
gem 'mustache'
gem 'nokogiri'
gem 'omniauth'
gem 'omniauth-openid'
gem 'openid-redis-store'
gem 'omniauth-facebook'
gem 'omniauth-twitter'
gem 'omniauth-instagram'

# forked while https://github.com/intridea/omniauth-github/pull/41 is being upstreamd
gem 'omniauth-github-discourse', require: 'omniauth-github'

gem 'omniauth-oauth2', require: false
gem 'omniauth-gitlab', '1.0.2'

gem 'omniauth-google-oauth2'
gem 'oj'
gem 'pg'
gem 'pry-rails', require: false
gem 'r2', '~> 0.2.5', require: false
gem 'rake'


gem 'rest-client'
gem 'rinku'
gem 'sanitize' 
gem 'sass'
gem 'sass-rails'
gem 'sidekiq'
gem 'sidekiq-statistic'

# for sidekiq web
gem 'sinatra', require: false
gem 'execjs', require: false
gem 'mini_racer'
gem 'thin', require: false
gem 'highline', require: false
gem 'rack-protection' # security

# Gems used only for assets and not required
# in production environments by default.
# allow everywhere for now cause we are allowing asset debugging in prd
group :assets do
  gem 'uglifier'
  gem 'rtlit', require: false # for css rtling
end

group :test do
  gem 'fakeweb', '~> 1.3.0', require: false
  gem 'minitest', require: false
  gem 'timecop'
end

group :test, :development do
  gem 'rspec'
  gem 'mock_redis'
  gem 'listen', '0.7.3', require: false
  gem 'certified', require: false
  # later appears to break Fabricate(:topic, category: category)
  gem 'fabrication', '2.9.8', require: false
  gem 'discourse-qunit-rails', require: 'qunit-rails'
  gem 'mocha', require: false
  gem 'rb-fsevent', require: RUBY_PLATFORM =~ /darwin/i ? 'rb-fsevent' : false
  gem 'rb-inotify', '~> 0.9', require: RUBY_PLATFORM =~ /linux/i ? 'rb-inotify' : false
  gem 'rspec-rails', require: false
  gem 'shoulda', require: false
  gem 'rspec-html-matchers'
  gem 'spork-rails'
  gem 'pry-nav'
  gem 'byebug', require: ENV['RM_INFO'].nil?
end

group :development do
  gem 'bullet', require: !!ENV['BULLET']
  gem 'better_errors'
  gem 'binding_of_caller'
  gem 'annotate'
  gem 'foreman', require: false
end

# this is an optional gem, it provides a high performance replacement
# to String#blank? a method that is called quite frequently in current
# ActiveRecord, this may change in the future
gem 'fast_blank' #, github: "SamSaffron/fast_blank"

# this provides a very efficient lru cache
gem 'lru_redux'

gem 'htmlentities', require: false

# IMPORTANT: mini profiler monkey patches, so it better be required last
#  If you want to amend mini profiler to do the monkey patches in the railties
#  we are open to it. by deferring require to the initializer we can configure discourse installs without it

gem 'flamegraph', require: false
gem 'rack-mini-profiler', require: false

gem 'unicorn', require: false
gem 'puma', require: false
gem 'rbtrace', require: false, platform: :mri
gem 'gc_tracer', require: false, platform: :mri

# required for feed importing and embedding
#
gem 'ruby-readability', require: false
gem 'simple-rss', require: false

gem 'stackprof', require: false, platform: :mri
gem 'memory_profiler', require: false, platform: :mri

gem 'rmmseg-cpp', require: false

gem 'logster'
