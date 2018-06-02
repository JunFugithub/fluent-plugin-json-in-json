# fluent-plugin-json-in-json

## Requirements

| fluent-plugin-json-in-json| Fluentd     | Ruby   |
|---------------------------|-------------|--------|
| >= 1.0.0                  | >= v0.14.0  | >= 2.1 |
|  < 1.0.0                  | >= v0.12.0  | >= 1.9 |

This fluentd parser plugin parses JSON log lines with nested JSON strings. For
example, given a docker log of ``{"log": "{\"foo\": \"bar\"}"}``, the log record
will be parsed into ``{:log => { :foo => "bar" }}``.

## Installation

Add this line to your application's Gemfile:

    gem 'fluent-plugin-json-in-json'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install fluent-plugin-json-in-json


## Usage

```
<source>
  type tail
  path /var/lib/docker/containers/*/*-json.log
  pos_file /var/log/fluentd-docker.pos
  time_format %Y-%m-%dT%H:%M:%S
  tag docker.*
  format json_in_json
  read_from_head true
</source>
```

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
