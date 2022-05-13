# Instructure

```bash
composer require socialiteproviders/instructure
```

## Installation & Basic Usage

Please see the [Base Installation Guide](https://socialiteproviders.com/usage/), then follow the provider specific instructions below.

### Add configuration to `config/services.php`

```php
'instructure' => [    
  'client_id' => env('INSTRUCTURE_CLIENT_ID'),  
  'client_secret' => env('INSTRUCTURE_CLIENT_SECRET'),  
  'redirect' => env('INSTRUCTURE_REDIRECT_URI'),
  'instance_url' => env('INSTRUCTURE_INSTANCE_URL')
],
```

### Add provider event listener

Configure the package's listener to listen for `SocialiteWasCalled` events.

Add the event to your `listen[]` array in `app/Providers/EventServiceProvider`. See the [Base Installation Guide](https://socialiteproviders.com/usage/) for detailed instructions.

```php
protected $listen = [
    \SocialiteProviders\Manager\SocialiteWasCalled::class => [
        // ... other providers
        \SocialiteProviders\Instructure\InstructureExtendSocialite::class.'@handle',
    ],
];
```

### Usage

You should now be able to use the provider like you would regularly use Socialite (assuming you have the facade installed):

```php
return Socialite::driver('instructure')->redirect();
```

### Returned User fields

- ``id``
- ``name``
- ``email``