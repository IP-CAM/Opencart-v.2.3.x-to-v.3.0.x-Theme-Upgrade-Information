#Upgrading themes from 2.3 to 3.0

Below I have created some regular expression code to help with your PHP IDE to mass search and replace basic PHP syntax with Twig syntax.

<hr>

```php
<?php echo $var; ?>
```

```php
<\?php echo [$](\w*\b)[;] \?\>
```

```php
{{ $1 }}
```

<hr>

```php
<?php echo $error_name[$language['language_id']]; ?>
```

```php
<\?php\s+echo\s+[$](\w+)\[[$](.*)\[\'(.*)\'\]\]\; \?\>
```

```php
{{ $1[$2.$3] }}
```

<hr>






