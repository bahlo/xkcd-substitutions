fs = require 'fs'
path = require 'path'
{spawn, exec} = require 'child_process'

src = 'src'
targets = [
  'chrome'
  'safari/xkcd-substitutions.safariextension'
  'firefox/data'
]

task 'build', 'compile source', ->
  Array.prototype.forEach.call targets, (target) ->
    build src, target

launch = (cmd, options=[], callback) ->
  app = spawn cmd, options
  app.stdout.pipe(process.stdout)
  app.stderr.pipe(process.stderr)
  app.on 'exit', (status) ->
    if status is 0
      callback?()
    else
      process.exit status

build = (from, to, callback) ->
  options = ['-c', '-o', to, from]
  launch 'coffee', options, callback
