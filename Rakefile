# frozen_string_literal: true

require "rspec/core/rake_task"
require "rubocop/rake_task"

RuboCop::RakeTask.new
RSpec::Core::RakeTask.new(:spec)

namespace :dummy do
  require_relative "spec/dummy/config/application"
  Dummy::Application.load_tasks
end

task(:spec).clear
desc "Run specs other than spec/acceptance"
RSpec::Core::RakeTask.new("spec") do |task|
  task.exclude_pattern = "spec/acceptance/**/*_spec.rb"
  task.verbose = false
end

desc "Run acceptance specs in spec/acceptance"
RSpec::Core::RakeTask.new("spec:acceptance") do |task|
  task.pattern = "spec/acceptance/**/*_spec.rb"
  task.verbose = false
end

desc "Run the specs and acceptance tests"
task default: %w(rubocop spec spec:acceptance)
