# NAME

Kelp::Module::MongoDB - Use MongoDB within Kelp

# DESCRIPTION

[Kelp::Module::MongoDB](http://search.cpan.org/perldoc?Kelp::Module::MongoDB) is a [Kelp](http://search.cpan.org/perldoc?Kelp) plugin.

# SYNOPSIS

First ...

      # conf/config.pl
    {
          modules      => ['MongoDB'],
          modules_init => {
              MongoDB => {
                  host => 'localhost',           # example
                  port => 27017,                 # example
              }
          }
      }

Then ...

    package MyApp;
    use Kelp::Base 'Kelp';

    sub some_route {
        my $self       = shift;
        my $db         = $self->mongodb->get_database('foodb');
        my $collection = $db->get_collection('bar');
        my $id         = $collection->insert({some => 'data'});
        my $data       = $collection->find_one({_id => $id});
    }





# METHODS

This module registers only one method into the application: `mongodb`.
It is an instance of a [MongoDB](http://search.cpan.org/perldoc?MongoDB) class.

# AUTHOR

Adam Stokes <adamjs@cpan.org>

# COPYRIGHT

Copyright 2013- Adam Stokes

# LICENSE

Licensed under the same terms as Perl.

# SEE ALSO

[Kelp](http://search.cpan.org/perldoc?Kelp).
