![Logo](https://www.aspec.es/cms/files/ASPEC_WORKOUT_EVENTS_Logo_460x300.jpg)

Bot de la seguridad social
===========================
Desarrollado por Andrei Garc�a Cuadra para Workout.
___

Workout realiza un n�mero ingente de movimientos y consultas en la Seguridad Social (S.S.) para la gesti�n de los periodos de alta de sus empleados. Estos movimientos y consultas pueden comunicarse a la S.S. por portal y por la aplicaci�n Winsuite. 

Por lo general los movimientos se llevan a cabo en el portal por la inmediatez de la confirmaci�n del movimiento, teniendo un retraso de varias horas en el caso de Winsuite. Esta comunicaci�n se realiza de forma manual, rellenando un formulario por cada movimiento o consulta y confirmando visualmente el resultado. 

Workout requiere de una herramienta de automatizaci�n que permita realizar esta labor mec�nica de comunicaci�n y consulta de movimientos, a partir de los movimientos y necesidad de informaci�n de la herramienta de gesti�n. 

___

El bot procesa peticiones mediante peticiones web (PHP WEB).
Estas peticiones son, mediante concurrencia, procesadas internamente por el bot (PHP CLI).
Para procesar dichas peticiones, se hace uso de Selenium Webdriver con un navegador Chrome headless.

C�digos de respuesta a peticiones HTTP:
```
200 - Petici�n satisfactoria
400 - Error de entrada (cliente)
500 - Error interno
```
> Todas las respuestas llevan asociado un mensaje en el body.
> Este mensaje es compartido para cada operaci�n y delimita su estado.

# Documentaci�n completa: [/docs](https://bitbucket.org/andreiwo/ss-bot/src/master/docs)

Ejemplo de petici�n HTTP:
```
POST /alta
	{
		"naf": "701111111111",
		"ipf": "01234567891",
		"reg": "0111",
		"ccc": "2811149794464",
		"nac": "14/11/1998",
		"sexo": "V",
		"tel": "685848171"
	}

RESPUESTA:
400 - MISSING_FIELDS
```
Otro ejemplo de petici�n HTTP, pero esta vez si el servidor va mal:
```
POST /alta
	{
		"naf": "701111111111",
		"ipf": "01234567891",
		"reg": "0111",
		"ccc": "2811149794464",
		"nac": "14/11/1998",
		"sexo": "V",
		"tel": "685848171"
	}

RESPUESTA:
500 - SELENIUM_RELOADING_CRASHED
```