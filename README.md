#Upgrading themes from 2.3 to 3.0

Below I have created some regular expression code to help with your PHP IDE to mass search and replace basic PHP syntax with Twig syntax.

```php
<?php echo $var; ?>
```
```php
<\?php echo [$](\w*\b)[;] \?\>
```
```php
{{ $1 }}
```







