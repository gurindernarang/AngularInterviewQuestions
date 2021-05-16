# Angular Interview Questions

Angular Interview Questions with examples

**1. What is difference b/w AngularJS and Angular?**

- AngularJS is Javascript based framework where as Angular is based on Typescript. Typescript is a superset of ES6,
  which is backward compatible with ES5.
- AngularJS based javascript uses terms of scope and controller while Angular uses hierarchy of components. Angular is
  component based(here component is directive with a template), while AngularJS uses directives.
- AngularJS is MVC based framework while Angular is service/controller based.
- AngularJS does not provide mobile support while Angular supports mobile.
- In AngularJS {{}} and special methods(ng-bind) are used to bind data between view and mode, where as in Angular ()
  and [] attributes are used to bind data between view and model.
- Dependency Injection is not used in AngularJS where as Hierarchical DI system is used in Angular.

Reference: https://stackify.com/angular-vs-angularjs-differences-between-angular-and-angularjs/

**2. What is a data binding?**

Data binding is a core concept in Angular and allows to define communication between a component and the DOM. Data
binding automatically keeps your page up-to-date based on your application's state.

There are four forms of data binding(divided as 3 categories) which differ in the way the data is flowing.

1. **From the Component to the DOM:**

   **Interpolation:** {{ value }}: Adds the value of a property from the component

   **Property binding:** [property]=”value”: The value is passed from the component to the specified property or
   simple HTML attribute

2. **From the DOM to the Component:**

   **Event binding:** (event)=”function”: When a specific DOM event happens (eg.: click, change, keyup), call the
   specified method in the component

3. **Two-way data binding:** [(ngModel)]=”value”:

   Two-way data binding allows to have the data flow both ways. For example, in the below code snippet, both the
   email DOM input and component email property are in sync

**3. What are building blocks in angular?**

There are basically 8 building blocks of Angular. These are:

1. Modules
2. Components
3. Templates
4. Metadata
5. Data binding
6. Directives
7. Services
8. Dependency

**4. What is difference b/w ng-content, ng-container and ng-template?**

**ng-content:** Suppose we have an html file in which we call a component/directive. Below is our html file content and "demostrate" is our component's selector

```html
<p>ng-content demonstration</p>
<demonstrate></demonstrate>
```

so what angular do is find this component and replaces the view attached to the component with "demostrate" tag. Suppose following is the content of "demonstrate" tag.

```html
<h1>Have patience!!!</h1>
```

Now what is we put in some content inside **demonstrate** tag??

```html
<p>ng-content demonstration</p>
<demonstrate>Some Content over here</demonstrate>
```

Nothing happens, it still do the same. What if we want to show this content? So this is where the ng-content directive comes in picture. What we need to do is, just add "ng-content" inside the component template and it will find the content inside the directive tag and add it to that template at that particular place where we added "ng-content" tag.

```html
<h1>Have patience!!!</h1>
<ng-content></ng-content>
```

So here ng-content tag gets replace with "Some Content over here".

In AngularJS we have "ng-transclude" for the same.

check this link for a POC of ng-content https://stackblitz.com/edit/angular-ivy-1pgb9z

**ng-container:** What if we need to add ngIf and ngFor both on the same div??

```
<div class="user" *ngIf="users" *ngFor="let user of users">
</div>
```

This will return an error as it's not possible to apply two structural directives to the same element and how we can resolve this error is, by added an extra div. So our code looks like this.

```
<div *ngIf="users">
  <div class="user" *ngFor="let user of users">
  </div>
</div>
```

Now what if we want to remove the extra div? So what we can do here, we can use ng-container instead of extra div.

```
<ng-container *ngIf="users">
  <div class="user" *ngFor="let user of users">
  </div>
</ng-container>
```

**ng-template:** Like the name indicates, the ng-template directive represents an Angular template: this means that the content of this tag will contain part of a template, that can be then be composed together with other templates in order to form the final component template. Benefits of ng-template is that it doesn't add content to the DOM.

Using ng-template we can implement if-else in a clean way. Suppose we have a list of student and we need to display that list in a tabular form and if the list is epmty we need to show a message. So we can do this using ng-template. Here is an example

```
<ul>
  <ng-container class="student" *ngIf="student" else NoRecordFound>
    <li *ngFor="let student of students">
      {{student.name}}
    </li>
  <ng-contianer>
</ul>
<ng-template #NoRecordFound>
  <h2>There is no record found!!!</h2>
</ng-template>
```

Reference:

https://blog.angular-university.io/angular-ng-template-ng-container-ngtemplateoutlet/

**5. How to improve performace of "ngForOf" or "\*ngFor" loop?**

The ngForOf directive is generally used in the shorthand form *ngFor.
Here is how we can use ngForOf instead of *ngFor

```
<li *ngFor="let item of items; index as i; trackBy: trackByFn">...</li>
```

we can also write above statement as

```
<ng-template ngFor let-item [ngForOf]="items" let-i="index" [ngForTrackBy]="trackByFn">
  <li>...</li>
</ng-template>
```

DOM manipulation is a very expensive operation, trackBy gives us the power to render the DOM/component partially depending on the change. A trackBy attribute allows us to define function that returns a unique identifier for each iterable element. This helps bypass unnecessary and expensive comparisons when the data list changes. Now when you change the collection, Angular can track which items have been added or removed according to the unique identifier and create or destroy only the items that changed.

Reference:

https://angular.io/api/common/NgForOf#description

https://www.youtube.com/watch?v=rz5K4oPIjME

**6. How are types of directive in angular?**
