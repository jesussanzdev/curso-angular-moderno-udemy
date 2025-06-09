# Angular Moderno con Dominicode

Bienvenido al repositorio del curso de Angular Moderno con Dominicode. Aquí aprenderás a construir aplicaciones modernas utilizando Angular y las mejores prácticas de la industria.

## Introducción

Este curso está diseñado para desarrolladores que desean mejorar sus habilidades en Angular y aprender a utilizar herramientas modernas como Nx para la gestión de proyectos.

## Requisitos

- Conocimientos básicos de JavaScript y TypeScript
- Familiaridad con Angular
- Node.js y npm instalados en tu máquina

## Comenzando

Para iniciar el servidor de desarrollo de tu aplicación, utiliza:

```sh
npx nx serve angular-moderno-udemy
```

Para crear un paquete de producción:

```sh
npx nx build angular-moderno-udemy
```

## Añadir nuevos proyectos

Puedes añadir nuevos proyectos a tu espacio de trabajo utilizando los plugins de Nx. Para generar una nueva aplicación, usa:

```sh
npx nx g @nx/angular:app demo
```

Para generar una nueva librería:

```sh
npx nx g @nx/angular:lib mylib
```

## Configuración de CI

Conecta tu proyecto a Nx Cloud para un CI rápido y escalable:

```sh
npx nx connect
```

Configura un flujo de trabajo de CI para tu espacio de trabajo:

```sh
npx nx g ci-workflow
```

## Instalar Nx Console

Nx Console es una extensión para editores que mejora tu experiencia de desarrollo. Está disponible para VSCode e IntelliJ.

[Instalar Nx Console &raquo;](https://nx.dev/getting-started/editor-setup?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

## Recursos útiles

- [Documentación de Angular](https://angular.io/docs)
- [Documentación de Nx](https://nx.dev)
- [Comunidad de Nx en Discord](https://go.nx.dev/community)

## Conéctate con Dominicode

- [Canal de YouTube de Dominicode](https://www.youtube.com/@Dominicode)
- [Síguenos en Twitter](https://twitter.com/Dominicode)
- [Únete a nuestro grupo en LinkedIn](https://www.linkedin.com/in/dominicode)

¡Esperamos que disfrutes del curso y aprendas mucho sobre Angular moderno!



## Notas:

//TODO
Para cargar nuevas rutas lazy loading, es necesario usar la funcion loadingComponent en los routeChild y loadChildren

const routes: Routes = [
  {
    path: '',
    loadComponent: () => import('./checkout.component'),
  },
];
export default routes;

//TODO
Con los standalone components hacer uso de : provideHttpClient() en lugar de HttpClientModule. 

//Mejora rendimiento y optimización en el tree shaking, ya que el HttpClientModule importaba mucha más información.

Se empieza a usar withFetch, withInterceptors y un montón de funciones nativas de javascript que están más optimizadas de las que facilitaba angular.

Hacer uso de los Interceptores funcionales en lugar de los interceptores de clase. Lo que se busca es que sean más claros y fáciles de usar, así como una mejora de rendimiento.

//TODO:
Migración de Interceptores

//TODO:
@let: permite declarar variables locales directamente en las plantillas de componentes: (disponible 100% en Angular 19)
@if similar al anterior
@switch similar al anterior, la condición evaluada es de tres iguales ===
@for, fuerza a usar un id por elemento: @for (item of items; track item.id){}


## Signals

A partir de la versión 17.1

Contenedor de un valor. El contenedor notificará a sus seguidores cuando el valor cambie.

Las signals pueden ser de solo escritura y de solo lectura. Las signals suelen sustituir a Inputs y Outputs en nuevas versiones.

Computer signals: signals que calculan su valor en función de otras signals.

name = input.required<string, string>({
  alias: 'title',
  transform: toCapitalize
})

Luego para leer su valor:

Hello: {{ name() }}

Con output seria similar:

messageEvent = output<string>();

## Effect:

Los efectos en angular signals son funciones reactivas diseñadas para ejecutar logica que depende de una o mas signals

## Zoneless:

¿Por qué abandonar zone.js?

- Mejora de rendimiento: zone.js no conoce el estado de la aplicación dispara procesos de forma innecesaria para estar siempre informado. 
- Core web vitals: Complementariamente el paquete es bastante pesado. Al eliminarlo mejorar las core vitals.
- Mejor experiencia e depuración
- Compatibilidad: al eliminar zone.js se quita una dependencia que no es ideal para algunos tipos de aplicaciones: async / await





