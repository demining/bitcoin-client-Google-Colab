= bitcoin-client {<img src="https://travis-ci.org/sinisterchipmunk/bitcoin-client.png?branch=master" alt="Build Status" />}[https://travis-ci.org/sinisterchipmunk/bitcoin-client] {<img src="https://codeclimate.com/github/sinisterchipmunk/bitcoin-client.png" />}[https://codeclimate.com/github/sinisterchipmunk/bitcoin-client] {<img src="https://coveralls.io/repos/sinisterchipmunk/bitcoin-client/badge.png" alt="Coverage Status" />}[https://coveralls.io/r/sinisterchipmunk/bitcoin-client]

Provides a Ruby library to the complete Bitcoin JSON-RPC API. Implements all methods listed
at {https://en.bitcoin.it/wiki/Original_Bitcoin_client/API_Calls_list}[https://en.bitcoin.it/wiki/Original_Bitcoin_client/API_Calls_list].
Also supports customizing the host and port number to connect to.



==
= Run Google Colab

https://colab.research.google.com/drive/1OShIMVcFZ_khsUIBOIV1lzrqAGo1gfm_?usp=sharing

==


== Installation

On Ruby 1.9, you can just install the gem and start using it. On 1.8, the 'json' gem is also required, so you'll need to install that first:

  gem install json

Or, if you're using Bundler (and you should be), just add it to the Gemfile:

  gem 'json', '~> 1.5.3'

== Usage

As with most Ruby gems, you first need to require the library into your project:

  require 'bitcon_client'

After doing this, the simplest possible usage looks like this:

  BitcoinClient('username', 'password').balance
  # => 0.001

Or, if you prefer a somewhat more explicit representation, the following code performs the exact
same task:

  client = BitcoinClient::Client.new('username', 'password')
  client.balance
  # => 0.001
  
The third and final way to use the library is by taking advantage of a simple DSL:

  include BitcoinClient
  
  # set up credentials
  username 'username'
  password 'password'
  
  balance
  # => 0.001
  
  accounts
  # => {"account" => 0.001}
  
The RPC method names available to you are exactly the same as those listed on the Bitcoin wiki
(again, that's {https://en.bitcoin.it/wiki/Original_Bitcoin_client/API_Calls_list}[https://en.bitcoin.it/wiki/Original_Bitcoin_client/API_Calls_list]). Some aliases
have been added to make them more "ruby-ish," but none of the original names have been changed.


== Host, Port and SSL

Here are several examples of how you can change the host information:

  BitcoinClient('username', 'password', :host => 'example.com', :port => 38332, :ssl => true)
  
  client = BitcoinClient::Client.new('username', 'password', :host => 'example.com')
  client.port = 38332
  client.ssl = true
  client.ssl?
  # => true
  
  include BitcoinClient
  host 'example.com'
  port 38332
  ssl?
  # => false
  ssl true
  ssl?
  # => true

You should see the BitcoinClient::Client class documentation if you'd like to see the other options and methods
that are made available.


== Donations

If you found this library useful and feel inclined to compensate me for my trouble, I'm certainly not going to turn you down!



----



----

|  | Donation Address |
| --- | --- |
| ??? __BTC__ | 1Lw2kh9WzCActXSGHxyypGLkqQZfxDpw8v |
| ??? __ETH__ | 0xaBd66CF90898517573f19184b3297d651f7b90bf |

