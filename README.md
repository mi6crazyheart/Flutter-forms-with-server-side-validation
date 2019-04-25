# Flutter forms with server-side validation

Here is a simple flutter form tutorial where I've shown 
- how to create flutter forms & send form data to the server. 
- how to receive the server response in flutter app & take action accordingly.

Youtube explanation video: https://youtu.be/A-CIeC743pA

## Server side - Login.php

	<?php
	$sampleUsersData = [
		[
			'name'=>'tom',
			'password'=>'12345',
		],
		[
			'name'=>'alex',
			'password'=>'67890',
		]
	];

	$username = $_POST['username'];
	$password = $_POST['password'];

	$userFound = false;
	foreach ($sampleUsersData as $key => $value) {
		if($value['name'] == $username && $value['password'] == $password ) {
			$userFound = true;
			break;
		}
	}

	$response = new stdClass;
	$response->status = null;
	$response->message = null;

	if($userFound) {
		$response->status = true;
		$response->message = 'valid user';
	} else {
		$response->status = false;
		$response->message = 'invalid user';
	}

	header('Content-Type: application/json');
	echo json_encode($response);

