
# Angular Interview Questions - Components Focus

## Beginner Level

### What is a Component in Angular?

A component is a fundamental building block of Angular applications. It controls a part of the screen (or view) and consists of an HTML template, a class for handling logic, and styling (CSS/SCSS).

### What is the purpose of the `@Component` decorator?

The `@Component` decorator marks a class as an Angular component and provides metadata, such as the component’s selector, template, and styles, which tell Angular how to create and use the component.

### What is the structure of an Angular component?

An Angular component consists of three parts:
- **Template (HTML):** Defines the view.
- **Class (TypeScript):** Contains the logic and data.
- **Styles (CSS/SCSS):** Defines the styling of the view.

### What is the role of the `selector` in a component?

The `selector` specifies how the component can be included in an HTML template. It acts like a custom HTML tag to represent the component.

### How do you define a component's template inline versus an external template?

You can define a template inline using `template: '<p>Some HTML</p>'` or reference an external file using `templateUrl: './component.html'`.

### How do you add styles to an Angular component?

Styles can be added inline using `styles: ['h1 { color: red; }']` or via an external file using `styleUrls: ['./component.css']`.

### What is `ngOnInit` in a component?

`ngOnInit` is a lifecycle hook that is called after the component has been initialized, often used to perform initialization tasks like fetching data.

### How do you include a component inside another component?

You can include a component by using its `selector` in the parent component's template, like `<app-child-component></app-child-component>`.

### What are component inputs and outputs?

- **Inputs:** Allow data to be passed into a component from its parent.
- **Outputs:** Allow the component to emit events to the parent component.

### How can you create a child component in Angular CLI?

You can create a child component using the Angular CLI command: `ng generate component component-name` or `ng g c component-name`.

---

## Intermediate Level

### What is the difference between a container and a presentational component?

A **container component** handles business logic, fetching data, and coordinating other components. A **presentational component** is focused on rendering UI and is typically stateless.

### How do you handle component communication?

Components can communicate through `@Input()` for receiving data and `@Output()` with `EventEmitter` for sending events to parent components.

### What are Angular component lifecycle hooks?

Lifecycle hooks are special methods that provide visibility into key moments of a component’s life, like `ngOnInit()`, `ngOnChanges()`, `ngAfterViewInit()`, `ngOnDestroy()`, etc.

### What is `ChangeDetectionStrategy` in Angular components?

`ChangeDetectionStrategy` defines how Angular checks for changes in the component. The two strategies are:
- **Default:** Angular checks the entire component tree on each event.
- **OnPush:** Angular checks only when an `@Input` reference changes.

### What is a `ViewChild` in Angular?

`ViewChild` is a decorator used to access a child component, directive, or DOM element in a parent component’s class.

### What is a `ContentChild` in Angular?

`ContentChild` is similar to `ViewChild`, but it is used to access projected content (content passed from parent to child via `<ng-content>`).

### What is `ng-content` and how is it used?

`ng-content` is used to project content from a parent component into a child component's template, enabling content transclusion.

### What is a dynamic component and how do you create one in Angular?

A dynamic component is created and inserted into the DOM at runtime using Angular’s `ComponentFactoryResolver` and `ViewContainerRef`.

### How do you pass complex data structures like objects or arrays to components using `@Input`?

You can pass objects and arrays directly to components using `@Input`, but you should ensure the input is immutable or use `ChangeDetectionStrategy.OnPush` for better performance.

### What is Angular Material and how does it enhance components?

Angular Material is a UI component library that provides pre-built, reusable UI components following Google’s Material Design guidelines, enhancing component design and functionality.

---

## Advanced Level

### What is a `HostListener` and how is it used in a component?

`HostListener` is a decorator that listens to DOM events from the host element of a directive or component. For example, `@HostListener('click')` listens to click events.

### What is a `HostBinding` and when would you use it?

`HostBinding` is a decorator used to bind a property of the host element to a value in the component or directive, such as binding classes or styles dynamically.

### How do you implement lazy loading of components in Angular?

Lazy loading of components can be achieved by dynamically importing the component when required using Angular’s `loadChildren` or dynamic `import()` syntax.

### What are structural directives in Angular, and how do they relate to components?

Structural directives, such as `*ngIf` and `*ngFor`, alter the structure of the DOM by adding or removing elements based on conditions or iteration. They can be applied to Angular components to conditionally render or loop over elements.

### How do you optimize the performance of Angular components?

Performance optimizations include using `OnPush` change detection, lazy loading, avoiding unnecessary DOM updates, and using `trackBy` with `ngFor` to improve rendering.

### What is the difference between `ngAfterViewInit` and `ngAfterContentInit`?

- **ngAfterViewInit:** Called after the component's view and child views have been initialized.
- **ngAfterContentInit:** Called after Angular projects external content into the component.

### What are Angular elements and how are they related to components?

Angular Elements allow you to package Angular components as custom web elements that can be used in non-Angular applications.

### How do you inject dependencies into a component's constructor in Angular?

Angular’s dependency injection system provides instances of services to components via the component’s constructor. For example, `constructor(private service: MyService)` injects `MyService` into the component.

### How can you handle route-based component loading in Angular?

Route-based component loading can be handled by configuring Angular’s Router with routes that map URL paths to specific components using the `RouterModule.forRoot()` or `RouterModule.forChild()` methods.

### What are content projection slots and how are they used in Angular components?

Content projection slots enable you to define multiple `<ng-content>` tags with different selectors in the same component to project different pieces of content into different slots.