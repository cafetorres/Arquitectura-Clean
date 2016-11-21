Tarea
==============================

----

## Aplicaciones Moviles

#### Carlos Fernando Torres Luna

##### cf.torresluna@gmail.com 

--- 
---



# Arquitectura Clean

Surge con la problemática que en la mayoría de los desarrollos en los cuales existe un framework se encuentra más código que lo representa, en lugar del problema que está resolviendo, es decir la idea es centrarse en lo que tiene que hacer la aplicación como tal y es por ello que dice que debemos de pensar en él framework como el mecanismo de paso de mensajes hacia nuestro software, el cual se debe mirar como una herramienta o plugin de lo que queremos realizar.

El autor dice en varias de sus charlas que más que una arquitectura sólo son una serie de condiciones que se deben cumplir para que una arquitectura de considere ”clean”, solo son una serie de reglas que lo único que van a hacer es dividir el software en capas.


Lo único que nos dice es que hay que respetar la Dependency Rule: “El código fuente sólo puede apuntar hacia adentro“.

#### Entities
Son aquellos objetos que van a representar los actores importantes de la lógica de negocio de nuestra aplicación.

#### Use Cases
Están muy relacionados con las entidades y son los encargados de implementar lógica de negocio de nuestra aplicación, ya que van a orientar todas aquellas interacciones del flujo de datos y entidades dejando al framework fuera de todo esto (en nuestro caso el sdk android), también se conocen como interactores.

(En ingeniería de software un caso de uso se define como: “Una secuencia de interacciones que se encargan de modelar alguna acción que quiero que mi software realice”)

#### Interface Adapters
Convierten los datos en el formato más conveniente para los casos de uso y entidades. (De manera recurrente aqui encontraras controladores y presentadores.)

#### Frameworks and Drivers
Aquí es donde residen los detalles y todo ese conjunto de plataformas externas y herramientas como puede ser la UI, Web, DB , Devices, etc. Generalmente solo se deben comunicar con el siguiente círculo a su interior.





#### Presentation Layer
Es la capa en donde ocurre todo lo relacionado a cómo funcionan la vistas normalmente activities y fragmentos los cuales contienen lógica pero únicamente enfocada en cómo funciona la vistas es decir el que debo mostrarle al usuario y cuando debe hacerlo. Para lograr un mejor manejo de vistas en esta capa se suelen usar patrones de UI (en el ejemplo que he escrito encontrarás MVP).



#### Domain Layer
Toda la lógica de negocio ocurre en esta capa aquí solo lo enfocado a que tiene que hacer nuestra aplicación. Se encuentran entidades y casos de uso regularmente es solo código java (puede ser kotlin o scala es indiferente) y no hay ninguna dependencia android.

#### Data Layer
Es la capa en donde se obtienen todos los datos que necesita nuestra aplicación para funcionar y los datos pueden ser de proveídos por una base de datos, de la red o de la memoria o de donde nos imaginemos particularmente en android hacemos uso de Repository Pattern un patrón que permite abstraer el origen de datos en donde no va importar de donde vengan los datos lo importante es que seran obtenidos de algún lugar y podremos utilizarlos para hacer las acciones que tengamos que hacer.

Algo que valdría la pena mencionar es que cada capa tiene su propio modelo de datos ya que será más fácil de testar y modificar para lo que estaremos usamos mappers para estar cambiando objetos de datos a un objeto de dominio y de dominio a un objeto de nuestra vista no quiero indagar mucho aquí pero cuando veas el código te darás cuenta de lo útil que es.

#### Benefits of using Clean Architecture
Existe una cantidad muy grande de diversas arquitecturas algunas en las cuales Uncle Bob se ha basado son Hexagonal Architecture, Onion Architecture, Screaming Architecture y lo importante es que cada una de ellas varía en sus detalles de implementación pero todas son similares y tienen el mismo objetivo separar en capas nuestro software con la finalidad de darle flexibilidad.

Las principales aportaciones que esta arquitectura seguirá motivando son:

+ Independiente de frameworks
+ Testable
+ Independendiente de nuestra UI
+ Independendiente de nuestra DB
+ Independendiente de cualquier herramienta externa