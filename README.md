# Calcula Distancias en PHP 

Aqui hay una funcion muy util que calcula distancias de un punto A a un punto B usando latitudes y longitudes. La funcion puede regresar distancias en millas, kilometros o millas nauticas.

```php

function distance($lat1, $lon1, $lat2, $lon2, $unit) {  

	$theta = $lon1 - $lon2; 
	$dist = sin(deg2rad($lat1)) * sin(deg2rad($lat2)) +  cos(deg2rad($lat1)) * cos(deg2rad($lat2)) * cos(deg2rad($theta)); 
	$dist = acos($dist); 
	$dist = rad2deg($dist); 
	$miles = $dist * 60 * 1.1515; 
	$unit = strtoupper($unit); 

	if ($unit == "K") { 
		return ($miles * 1.609344); 
	} else if ($unit == "N") { 
		return ($miles * 0.8684); 
	} else { 
		return $miles; 
	} 
}

```

Uso

```php
echo distance(32.9697, -96.80322, 29.46786, -98.53506, "k")." kilometros";
```
