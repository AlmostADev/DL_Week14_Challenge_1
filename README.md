# Actividad 027 - CRUD anidado

- Para poder realizar este actividad debes haber realizado los cursos previos junto con los videos online correspondientes a la experiencia 14.

## El objetivo de esta actividad es la implementación de un CRUD anidado de Categorías y Productos, donde una categoría puede tener N cantidad de productos, y cada producto pertenece a una categoría (relación 1 a N).

## Ejercicio 1:

- Iniciar un nuevo proyecto en Rails 5.1 :heavy_check_mark:

- Añadir el **CDN de Boostrap** al layout :heavy_check_mark:

- Añadir el **CDN de jQuery** al layout :heavy_check_mark:

- Crear un scaffold **Category** con el campo *name* (string) :heavy_check_mark:

- Revisar y correr la migración :heavy_check_mark:

- Convertir el *index* de *categories* en la página de inicio. :heavy_check_mark:

- Crear un modelo **Product** con los campos *name* (string), *price* (integer) y *category:references*. :heavy_check_mark:

- Revisar y correr la migración. :heavy_check_mark:

- En el modelo *Category* agregar la relación con producto (**has_many**) y verificar que el modelo *Product* se haya creado con la relación correcta (**belongs_to**) :heavy_check_mark:

    > Recordar la relación entre categoría y producto en el enunciado.

- Crear el controller **products**. :heavy_check_mark:

- Generar la ruta para la creación de un producto asociado a una categoría. :heavy_check_mark:

    - Para ello modificar la ruta resources de Categories que ahora recibirá un bloque y dentro crearemos la ruta que apuntará al método create de products. :heavy_check_mark:
    
    ~~~ruby
    resources :products, only: [:create]
    ~~~

- En la terminal ejecutar **rails routes** para corroborar la ruta creada. La ruta generada debe contener el **:category_id** y apuntar al método **products#create**. :heavy_check_mark:

- Para poder almacenar un registro en el método create primero debemos generar el filtro de parámetros conocido como **strong params**, para ello: :heavy_check_mark:

    - En el controller **products** crear el método **product_params**. Este método debe permitir y retornar los campos necesarios para la creación de un nuevo producto, es decir, name y price. :heavy_check_mark:

- En el controller **products** crear el método **create**. Este método debe generar una nueva instancia de *Product* recibiendo como argumento **product_params** y almacenarlo en la BD. Luego redireccionar a la vista *show* de la categoría involucrada. :heavy_check_mark:

- En la vista *Show* de categories además del detalle de la categoría se debe agregar un formulario que permita ingresar un nuevo producto a la categoría seleccionada. :heavy_check_mark:

    - El formulario debe ser generado utilizando el helper *form_with* anidando los dos modelos y debe implementar las clases de bootstrap (revisar docs). :heavy_check_mark:

    ~~~ruby
    <%= form_with(model: [ @category, @product ]) do |form| %> :heavy_check_mark:
    ~~~

    - Donde **@product** debe ser declarado en el método correspondiente como una nueva instancia de **Product**. :heavy_check_mark:

    - El formulario debe tener campos para *name* y *price*. :heavy_check_mark:

- En la vista *show*, bajo el formulario, se deben listar todos los productos correspondientes a esa categoría en una tabla con los campos *name* y *price*. :heavy_check_mark:

- Junto a cada registro de producto en la tabla se debe añadir un botón para eliminar el producto. Para ello:

    - Agregar el método *destroy* a la ruta anidada. :x:

     ~~~ruby
     resources :products, only: [:create, :destroy] 
     ~~~

     - Crear el método correspondiente en el controller. :x:

     - Agregar el botón con el *method: :delete* a cada registro de productos en la tabla. :x:

- En la vista *Index* de *categories*: 
    - Los registros deben estar listados en una tabla (bootstrap) que contenga el nombre de la categoría y la cantidad de productos que existe por categoría (**count**). :x:

    - Al hacer click en el nombre de la categoría debe redireccionar a la vista *show* de esa categoría. :x:

    - Cada categoría ademas debe ir acompañada de botones para *Edit* y *Destroy* utilizando la clases de bootstrap. :x:

- En *application.html.erb*:
	- En una vista parcial, agregar un navbar (**fixed**) con bootstrap con los link para acceder al home (index de categorias) y para agregar nueva categoría. :x:
