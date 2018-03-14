# WireCipher
OpenSSL encrypt/decrypt for ProcessWire

I'm in no way an expert in security. When you realy need a secure script, do not use this module.

````php
<?php namespace ProcessWire;


$text = 'Aenean lacinia bibendum nulla sed consectetur. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. egestas eget quam.';

$cypher = $modules->get('WireCipher');

/**
 * Default
 *
 */
$encrypted = $cypher->encrypt($text);
$decrypted = $cypher->decrypt($encrypted);
echo $decrypted . "<br>";


/**
 * Query url
 *
 */
$encrypted = $cypher->encryptToGetVars($text);
$decrypted = $cypher->decryptFromGetVars($encrypted);
echo $decrypted . "<br>";


/**
 * urlSegments
 *
 */
$options = array(
	// Optional, throws when length encrypted text exceeds length urlSegments can handle.
	'throw' => true,
	// Optional, when set encrypted text will evenly shared over the number of segments given.
	'numSegments' => 5,
	// Optional defaults to string, other properties: WireInput and array
	'output' => 'string',
);

$encrypted = $cypher->encryptToUrlSegments($text, $options);
$decrypted = $cypher->decryptFromUrlSegments($encrypted);
echo $decrypted . "<br>";

````

Use at own risk,
have fun...
