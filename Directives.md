
# Top 20 Angular 18 Directives Interview Questions and Answers

## 1. What is a Directive in Angular?
**Answer:**  
A directive is a class with a `@Directive()` decorator that allows you to add behavior to elements in Angular. Directives can modify the DOM by adding or removing elements, changing styles, or listening to events.

**Example:**
```typescript
@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {
  constructor(private el: ElementRef) {
    el.nativeElement.style.backgroundColor = 'yellow';
  }
}
```

## 2. How many types of directives are there in Angular?
**Answer:**  
Angular provides three main types of directives:
- **Component Directives:** They are special types of directives with templates.
- **Attribute Directives:** These modify the appearance or behavior of an element.
- **Structural Directives:** They change the structure of the DOM (e.g., `ngIf`, `ngFor`).

## 3. What is the difference between Structural and Attribute directives?
**Answer:**  
- **Structural Directives** change the DOM layout by adding or removing elements (`*ngIf`, `*ngFor`).
- **Attribute Directives** change the appearance or behavior of an existing DOM element (`ngClass`, `ngStyle`).

## 4. How does `*ngIf` work in Angular?
**Answer:**  
`*ngIf` is a structural directive that conditionally includes or excludes a template from the DOM.

**Example:**
```html
<p *ngIf="isLoggedIn">Welcome, User!</p>
```

## 5. How does `*ngFor` work in Angular?
**Answer:**  
`*ngFor` is a structural directive used to loop through collections and render a template for each item.

**Example:**
```html
<ul>
  <li *ngFor="let item of items">{{ item }}</li>
</ul>
```

## 6. Explain `ngClass` directive in Angular.
**Answer:**  
`ngClass` is an attribute directive that adds or removes CSS classes on an element dynamically based on conditions.

**Example:**
```html
<div [ngClass]="{'active': isActive, 'disabled': isDisabled}">Button</div>
```

## 7. What is the `ngStyle` directive?
**Answer:**  
`ngStyle` is an attribute directive that applies dynamic styles to an element.

**Example:**
```html
<div [ngStyle]="{'color': color, 'font-size': size + 'px'}">Styled Text</div>
```

## 8. How do you create a custom attribute directive in Angular?
**Answer:**  
You can create a custom attribute directive by defining a class and decorating it with `@Directive` decorator.

**Example:**
```typescript
@Directive({
  selector: '[appBorder]'
})
export class BorderDirective {
  constructor(private el: ElementRef) {
    this.el.nativeElement.style.border = '1px solid black';
  }
}
```

## 9. What is the purpose of `Renderer2` in Angular Directives?
**Answer:**  
`Renderer2` is used to safely modify the DOM while ensuring compatibility with server-side rendering and web workers.

**Example:**
```typescript
constructor(private renderer: Renderer2, private el: ElementRef) {
  this.renderer.setStyle(this.el.nativeElement, 'color', 'blue');
}
```

## 10. Explain the `@HostListener` decorator in Angular.
**Answer:**  
`@HostListener` listens to DOM events from the host element and triggers actions within a directive.

**Example:**
```typescript
@HostListener('mouseenter') onMouseEnter() {
  this.highlight('yellow');
}
```

## 11. What is `@HostBinding` in Angular?
**Answer:**  
`@HostBinding` binds a DOM property to a directive/component property.

**Example:**
```typescript
@HostBinding('class.active') isActive = true;
```

## 12. How can you implement two-way data binding in a custom directive?
**Answer:**  
Use `@Output()` with an `EventEmitter` and `@Input()` properties.

**Example:**
```typescript
@Directive({
  selector: '[appTwoWay]'
})
export class TwoWayDirective {
  @Input() value: string;
  @Output() valueChange = new EventEmitter<string>();
}
```

## 13. How to pass input values to a directive?
**Answer:**  
Use the `@Input()` decorator to pass values from a component to a directive.

**Example:**
```typescript
@Directive({
  selector: '[appInput]'
})
export class InputDirective {
  @Input() appInput: string;
}
```

## 14. What is the role of `ngTemplateOutlet` directive?
**Answer:**  
`ngTemplateOutlet` is used to insert a template dynamically into a view.

**Example:**
```html
<ng-container *ngTemplateOutlet="templateRef"></ng-container>
```

## 15. Explain `*ngSwitch` in Angular.
**Answer:**  
`*ngSwitch` is a structural directive used to switch between multiple views based on a condition.

**Example:**
```html
<div [ngSwitch]="value">
  <p *ngSwitchCase="'one'">One</p>
  <p *ngSwitchCase="'two'">Two</p>
  <p *ngSwitchDefault>Other</p>
</div>
```

## 16. What is `ngModel` and how does it work in Angular?
**Answer:**  
`ngModel` is a directive for two-way data binding in template-driven forms.

**Example:**
```html
<input [(ngModel)]="name" />
<p>{{ name }}</p>
```

## 17. Explain `ngIfElse` in Angular.
**Answer:**  
You can use `ngIfElse` to display alternate templates based on a condition.

**Example:**
```html
<p *ngIf="isTrue; else elseBlock">True</p>
<ng-template #elseBlock>False</ng-template>
```

## 18. What is the difference between `ngContainer` and `ngTemplate`?
**Answer:**
- **ngContainer** is used for grouping elements without adding extra DOM nodes.
- **ngTemplate** is used to define a block of HTML that can be rendered later.

## 19. How to use `@ContentChild` in Angular directives?
**Answer:**  
`@ContentChild` is used to get a reference to projected content within a directive.

**Example:**
```typescript
@ContentChild('ref', { static: true }) refElement: ElementRef;
```

## 20. Explain `ng-content` and its use case in Angular directives.
**Answer:**  
`ng-content` is used for content projection, allowing developers to project content into a component or directive.

**Example:**
```html
<ng-content></ng-content>
```
