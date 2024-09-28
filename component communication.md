
# Top Interview Questions and Answers on Component Communication in Angular

## 1. What is Component Communication in Angular?
**Answer:**  
Component communication in Angular refers to the interaction between components, which can be parent-child, child-parent, or sibling-sibling. Angular provides several mechanisms to facilitate this communication, such as `@Input()`, `@Output()`, services, and `ViewChild`.

## 2. How can you pass data from a parent component to a child component?
**Answer:**  
You can pass data from a parent component to a child component using the `@Input()` decorator in Angular.

**Example:**
**Parent component:**
```html
<app-child [childProperty]="parentData"></app-child>
```
**Child component:**
```typescript
@Input() childProperty: string;
```

## 3. How does the `@Output()` decorator work in Angular?
**Answer:**  
The `@Output()` decorator is used to send data from a child component to its parent component. It works with the `EventEmitter` class to emit events.

**Example:**
**Child component:**
```typescript
@Output() notifyParent: EventEmitter<string> = new EventEmitter<string>();

sendMessage() {
  this.notifyParent.emit('Hello Parent');
}
```
**Parent component:**
```html
<app-child (notifyParent)="onNotify($event)"></app-child>
```

## 4. How can you share data between sibling components in Angular?
**Answer:**  
You can share data between sibling components using a shared service. The service can store the data and components can inject it to access the data.

**Example:**
**Shared Service:**
```typescript
@Injectable()
export class SharedService {
  private data = new BehaviorSubject<string>('default');
  currentData = this.data.asObservable();

  updateData(data: string) {
    this.data.next(data);
  }
}
```
**Sibling Component 1:**
```typescript
constructor(private sharedService: SharedService) {}

changeData() {
  this.sharedService.updateData('New data from Component 1');
}
```
**Sibling Component 2:**
```typescript
constructor(private sharedService: SharedService) {
  this.sharedService.currentData.subscribe(data => this.data = data);
}
```

## 5. What is `ViewChild` in Angular and how is it used for component communication?
**Answer:**  
`ViewChild` allows a parent component to access a child component's properties and methods. It is useful for direct communication from a parent to a child component.

**Example:**
**Parent component:**
```typescript
@ViewChild(ChildComponent) childComponent: ChildComponent;

callChildMethod() {
  this.childComponent.someMethod();
}
```
**Child component:**
```typescript
someMethod() {
  console.log('Child method called');
}
```

## 6. Explain `@ViewChildren` and when would you use it?
**Answer:**  
`@ViewChildren` is similar to `@ViewChild`, but it is used when you want to access multiple instances of child components or directives. It returns a `QueryList` that can be iterated over.

**Example:**
```typescript
@ViewChildren(ChildComponent) childComponents: QueryList<ChildComponent>;

callChildMethods() {
  this.childComponents.forEach(child => child.someMethod());
}
```

## 7. What is `ContentChild` and how is it different from `ViewChild`?
**Answer:**  
`ContentChild` is used to get a reference to a projected content in a component, whereas `ViewChild` is used to access child components or elements within the same template.

**Example:**
**Parent component:**
```html
<app-child>
  <p #projectedContent>Projected Content</p>
</app-child>
```
**Child component:**
```typescript
@ContentChild('projectedContent') content: ElementRef;

ngAfterContentInit() {
  console.log(this.content.nativeElement.textContent);
}
```

## 8. How can you pass data from parent to child using `ngOnChanges`?
**Answer:**  
`ngOnChanges` is a lifecycle hook that is called when the `@Input()` properties of a component change. It allows you to react to changes in the input properties.

**Example:**
**Child component:**
```typescript
@Input() data: string;

ngOnChanges(changes: SimpleChanges) {
  if (changes['data']) {
    console.log('Data changed:', this.data);
  }
}
```

## 9. What is a shared service in Angular? How can it facilitate communication between components?
**Answer:**  
A shared service is an Angular service that is used to store and share data between components. It uses dependency injection, making it easy for components to access the same data or logic.

**Example:**
```typescript
@Injectable({
  providedIn: 'root',
})
export class SharedService {
  private message = new Subject<string>();
  currentMessage = this.message.asObservable();

  changeMessage(message: string) {
    this.message.next(message);
  }
}
```

## 10. How does Angular EventEmitter work?
**Answer:**  
`EventEmitter` is used to emit custom events in Angular. It is typically used with the `@Output()` decorator to send data from a child component to a parent component.

**Example:**
```typescript
@Output() customEvent: EventEmitter<string> = new EventEmitter<string>();

triggerEvent() {
  this.customEvent.emit('Data from child');
}
```

## 11. How can you use `BehaviorSubject` for component communication?
**Answer:**  
`BehaviorSubject` is a type of RxJS subject that holds a current value and emits it to new subscribers immediately. It is commonly used for sharing data across multiple components.

**Example:**
```typescript
export class SharedService {
  private message = new BehaviorSubject<string>('Initial message');
  currentMessage = this.message.asObservable();

  changeMessage(newMessage: string) {
    this.message.next(newMessage);
  }
}
```

## 12. What is the difference between `Subject` and `BehaviorSubject` in Angular?
**Answer:**  
- **Subject:** It doesn’t store the current value and only emits new data to subscribers.
- **BehaviorSubject:** It stores the latest value and emits it immediately to any new subscribers.

## 13. What are `Output` and `EventEmitter` in Angular?
**Answer:**  
`@Output()` is used to pass events from child to parent components. `EventEmitter` is a class used to create events that can be emitted and listened to by the parent component.

## 14. How can you pass references to components using `@ViewChild`?
**Answer:**  
You can pass a reference to a child component using `@ViewChild`, which allows the parent component to access child component properties and methods.

## 15. Can you explain the use of `@ContentChildren` in Angular?
**Answer:**  
`@ContentChildren` is used to query multiple instances of projected content within a component.

**Example:**
```typescript
@ContentChildren('item') items: QueryList<ElementRef>;

ngAfterContentInit() {
  this.items.forEach(item => console.log(item.nativeElement.textContent));
}
```

## 16. What is a `Subject` in RxJS and how is it used for communication in Angular?
**Answer:**  
A `Subject` in RxJS is a special type of Observable that can multicast to multiple Observers. It is used to send data between components, especially for sibling communication.

## 17. What is the difference between `@ViewChild` and `@ViewChildren`?
**Answer:**  
`@ViewChild` is used to access a single child component or element, while `@ViewChildren` returns a `QueryList` of all matching children.

## 18. How to use `ngOnChanges` for component interaction?
**Answer:**  
`ngOnChanges` is called whenever the value of an input property changes. This can be used to react to data changes from the parent component.

## 19. Can services with `providedIn: root` share data between lazy-loaded modules?
**Answer:**  
Yes, services with `providedIn: 'root'` are singleton services available across the entire application, including lazy-loaded modules, and can be used to share data globally.

## 20. What is the best way to share state between components in Angular?
**Answer:**  
Using a shared service with RxJS `Subject`, `BehaviorSubject`, or other observable-based approaches is the best way to share state between components.