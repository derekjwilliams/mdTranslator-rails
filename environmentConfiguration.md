# Environment Confguration for use with RVM with JRuby and warbler (Debian Jessie or Ubuntu 16.04 or greater)


##run rvm first time if needed, but should be in .bash_profile

source $HOME/.rvm/scripts/rvm

You may see

`ruby-2.3.1,:engine=>jruby,:engine_version=>9.1.6.0 is not installed.`

*You can ignore the error since it appears that we have both ruby-2.3.1 and jruby installed; a rubyist may be able to fix this*

## install the correct ruby, in this case jruby-9.1.6.0 (see Gemfile)

rvm install jruby-9.1.6.0
rvm use jruby-9.1.6.0

## install the bundler (if needed)

gem install bundler

## install gems needed

bundle install

## Create the war

warble war

*The circular argument reference warning does not seem to be an issue when running*


## set the secret_key_base

export SECRET_KEY_BASE=[your secret key base]

*see http://stackoverflow.com/questions/23180650/how-to-solve-error-missing-secret-key-base-for-production-environment-rai or other resources*

## run in container, e.g. jetty runner

java -jar jetty-runner.jar mdTranslator-rails.war 

## Browse to web app

http://localhost:8080

Click on "demo" link to do some metadata translations

### Note

The css and js are not found, this is a known warbler issue https://github.com/jruby/warbler/issues/199  This does not affect functionality of the translations
