# Suppress a Member

Suppress a member from list mails

## Suppress a Member Options

[MadMimi's List All Members Documentation](https://madmimi.com/developer/lists) should give you an idea
of what you need to send to the API.  This options object makes some of the methods easier.

### Method Reference

`Suppress::setEmail($email)` - Sets the email to delete

## Exceptions

The following exceptions may be thrown throughout the duration of a options object.

- `MadMimi\Exception\InvalidOptionException` During options object creation, a value in the array of the constructor argument that's key was not defined as a protected property of this options class
