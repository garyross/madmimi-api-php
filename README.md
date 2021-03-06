# madmimi-api-php
An up-to-date PHP library for integrating with the MadMimi API.

Using your <http://madmimi.com> account, you can interact with all parts of the API using this library.  This library
requires PHP 5.4+ and curl to be installed.

## Installation

This library is available on packagist and can be installed using composer.

```bash
$ composer require aaronsaray/madmimi-api-php
```

## Basic Usage

This example sends a transactional email to a promotion named "Meaning of Life" and replaces the {answer} placeholder with
the answer to life, the universe and everything.  This email goes to Slartibartfast at iluvcoastlines@planetdesigners.com

```php
<?php

use MadMimi\Connection;
use MadMimi\CurlRequest;
use MadMimi\Options\Mail\Transactional;

$connection = new Connection('your@email.com', 'your-api-key', new CurlRequest());

$options = new Transactional();
$options->setPromotionName('Meaning of Life')
  ->setPlaceholderValues(['answer'=>'42'])
  ->setTo('iluvcoastlines@planetdesigners.com', 'Slartibartfast');

$transactionId = $connection->request($options);
```

## Documentation

### Core
 - [The Connection Object](docs/connection.md)
 
### Sending Mail
 - [Transaction Mail Options](docs/mail/transactional.md)
 - [Mailing List Options](docs/mail/mailing-list.md)
 - [Import and Send to Mailing List Options](docs/mail/import-mailing-list.md)
 - [Send to All Options](docs/mail/send-to-all.md)
 
### Statistics / Status
 - [Transaction Mail Status](docs/stats/transactional.md)
 - [Mailing Stats](docs/stats/mailing.md) 
 - [Sent Stats](docs/stats/sent.md) 
 - [Abused Stats](docs/stats/abused.md) 
 - [Bounced Stats](docs/stats/bounced.md) 
 - [Clicked Stats](docs/stats/clicked.md) 
 - [Forwarded Stats](docs/stats/forwarded.md) 
 - [Links Stats](docs/stats/links.md) 
 - [Read Stats](docs/stats/read.md) 
 - [Unsubscribed Stats](docs/stats/unsubscribed.md) 
 - [Transactional Count](docs/stats/transactional-count.md)
 - [Members Created Count](docs/stats/members-created-count.md)
 - [Promotion Attempts](docs/stats/promotion-attempts.md)
 
### Webforms
 - [List All](docs/webforms/all.md)
 - [Get Single](docs/webforms/single.md)
   
### Lists
 - [List All](docs/lists/all.md)
 - [Add List](docs/lists/add.md)
 - [Rename List](docs/lists/rename.md)
 - [Delete List](docs/lists/delete.md)
 - [Clear List](docs/lists/clear.md)
   
### Promotions
 - [List All](docs/promotions/all.md)
 - [Get Single](docs/promotions/single.md)
 - [Search](docs/promotions/search.md)
 - [Save](docs/promotions/save.md)
 - [Delete](promotions/delete.md)

### Members
 - [List All](docs/members/all.md)
 - [List All In a List](docs/members/all-by-list.md)
 - [Get Single](docs/members/single.md)
 - [Search](docs/members/search.md)
 - [Suppressed Since](docs/members/suppressed-since.md)
 - [Suppress](docs/members/all.md)
 - [Is Suppressed](docs/members/is-suppressed.md)
 - [Events Since](docs/members/events-since.md)
 - [Create](docs/members/create.md)
 - [Update Email](docs/members/update-email.md)
 - [Update](docs/members/update.md) 
 - [Get All List Subscriptions](docs/members/lists.md)
 - [Import CSV Members](docs/members/import.md)
 - [Import Status](docs/members/import-status.md)
 - [Add Member To List](docs/members/add-to-list.md)
 - [Remove Member From List](docs/members/remove-from-list.md)
 
### Addons
 - [List All](docs/addons/all.md)
 - [List User's](docs/addons/user.md)
 - [Toggle User's](doc/addons/toggle.md)
 - [List All Drip Campaigns](docs/addons/drip.md)
 
#### Google Analytics
 - [List All Domains](docs/addons/ga/all.md)
 - [Add a Domain](docs/addons/ga/add.md)
 - [Delete a Domain](docs/addons/ga/delete.md)
 
#### Social Links
 - [List All](docs/addons/sociallinks/all.md)
 - [List User's](docs/addons/sociallinks/user.md)
 - [Update User's](docs/addons/sociallinks/update.md)
   
#### Child Accounts
 - [List All](docs/addons/childaccounts/all.md)   
 - [Add](docs/addons/childaccounts/add.md)   
 - [Update](docs/addons/childaccounts/update.md)   
 - [Delete](docs/addons/childaccounts/delete.md)   
 - [Update List Permissions](docs/addons/childaccounts/permissions.md)   
   
### Misc
  
In general, method calls and organization of this API have been normalized using this library.  So, please check
the MadMimi documentation AND this code documentation before implementing a method.  Mostly they will translate the same, 
but from time to time there have been liberties taken in this library.  The responses are not currently translated into
known, normalized objects.

One such example is the transactional mailer status.  While this documentation is located under the mailer section, and
the end point contains the /mailer path, it has been moved to the stats section.  This particular call is not for sending
a mail, but instead, receiving the status of the particular email.  It seems to fit better with the statistics section.

Another example is the promotion search API.  The search functionality was split up - the search by exact ID is in the single
retrieval option - whereas the rest of the search criteria is in the search option.  This mirrors the webforms paradigm.
  
## About

### Requirements

 - PHP 5.4+
 - Curl
 - MadMimi mailer API access
 
### Bugs and Feature Requests

Bugs and feature request are tracked on [GitHub](https://github.com/aaronsaray/madmimi-api-php/issues)

### Author

Aaron Saray - <http://aaronsaray.com>

### License

This library is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

### Acknowledgements

We're using MadMimi in our work at <https://www.smallshopsunited.com> - stop by and check it out.  Also, special thanks
to the team at MadMimi who gave me access to the API for testing this library.  
