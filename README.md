# Angular Interview Questions & Answers

> Click :star:if you like the project. Pull Request are highly appreciated.

### Table of Contents

| No. | Questions |
|---- | ---------
|1 | [What is Angular?](#what-is-angular) |
|2 | [What is the difference between AngularJS and Angular?](#what-is-the-difference-between-angularjs-and-angular?)|
|3 | [What is typescript?](#what-is-typescript)|
|4 | [Write a pictorial diagram of Angular architecture?](#write-a-pictorial-diagram-of-angular-architecture)|
|5 | [What are the key components of Angular?](#what-are-the-key-components-of-angular?)|
|6 | [What are directives?](#what-are-directives)|
|7 | [What are components?](#what-are-components)|
|8 | [What are the differences between Component and Directive?](#what-are-the-differences-between-component-and-directive)|
|9 | [What is a template?](#what-is-a-template)|
|10| [What is a module?](#what-is-a-module?)|
|11| [What are lifecycle hooks available?](#what-are-lifecycle-hooks-available)|
|12| [What is a data binding?](#what-is-a-data-binding)|
|13| [What is metadata?](#what-is-metadata)|
|14| [What is angular CLI?](#what-is-angular-cli)|
|15| [What is the difference between constructor and ngOnInit?](#what-is-the-difference-between-constructor-and-ngoninit?)|
|16| [What is a service](#what-is-a-service)|
|17| [What is dependency injection in Angular?](#what-is-dependency-injection-in-angular)|
|18| [How is Dependency Hierarchy formed?](#how-is-dependency-hierarchy-formed)|
|19| [What is the purpose of async pipe?](#what-is-the-purpose-of-async-pipe)|
|20| [What is the option to choose between inline and external template file?](#what-is-the-option-to-choose-between-inline-and-external-template-file)|
|21| [What is the purpose of *ngFor directive?](#what-is-the-purpose-of-ngfor-directive)|
|22| [What is the purpose of ngIf directive?](#what-is-the-purpose-of-ngif-directive)|
|23| [What happens if you use script tag inside template?](#what-happens-if-you-use-script-tag-inside-template)|
|24| [What is interpolation?](#what-is-interpolation)|
|25| [What are template expressions?](#what-are-template-expressions)|
|26| [What are template statements?](#what-are-template-statements)|
|27| [How do you categorize data binding types?](#how-do-you-categorize-data-binding-types)|


1. ### What is Angular Framework?

    Angular is a **typeScript-based open-source** front-end platform that makes it easy to build applications with in web/mobile/desktop. The major features of this framework such as declarative templates, dependency injection, end to end tooling, and many more other features are used to ease the development.

2. ### What is the difference between AngularJS and Angular?
    Angular is a completely revived component-based framework in which an application is a tree of individual components.

    Some of the major difference in tabular form

    | AngularJS | Angular |
    |---- | ---------
    | It is based on MVC architecture  | This is based on Service/Controller |
    | This uses use JavaScript to build the application| Introduced the typescript to write the application |
    | Based on controllers concept| This is a component based UI approach|
    | Not a mobile friendly framework| Developed considering mobile platform|
    | Difficulty in SEO friendly application development| Ease to create SEO friendly applications|

3. ### What is typescript?
    TypeScript is a typed superset of JavaScript created by Microsoft that adds optional types, classes, async/await, and many other features, and compiles to plain JavaScript. Angular built entirely in TypeScript and used as a primary language.
    You can install it globally as
    ```
    npm install -g typescript
    ```
    Let's see a simple example of typescript usage,
    ```typescript
    function greeter(person: string) {
        return "Hello, " + person;
    }

    let user = "Sudheer";

    document.body.innerHTML = greeter(user);
    ```
    The greeter method allows only string type as argument.

4. ### Write a pictorial diagram of Angular architecture?
    The main building blocks of an Angular application is shown in the below diagram
    ![ScreenShot](images/architecture.png)

5. ### What are the key components of Angular?
    Angular has the below key components,
    1. **Component:** These are the basic building blocks of angular application to control HTML views.
    2. **Modules:** An angular module is set of angular basic building blocks like component, directives, services etc. An application is divided into logical pieces and each piece of code is called as "module" which perform a single task.
    3. **Templates:** This represent the views of an Angular application.
    4. **Services:** It is used to create components which can be shared across the entire application.
    5. **Metadata:** This can be used to add more data to an Angular class.

6. ### What are directives?
    Directives add behaviour to an existing DOM element or an existing component instance.
    ```typescript
    import { Directive, ElementRef, Input } from '@angular/core';

    @Directive({ selector: '[myHighlight]' })
    export class HighlightDirective {
        constructor(el: ElementRef) {
           el.nativeElement.style.backgroundColor = 'yellow';
        }
    }
    ```

    Now this directive extends HTML element behavior with a yellow background as below
    ```html
    <p myHighlight>Highlight me!</p>
    ```

7. ### What are components?
    Components are the most basic UI building block of an Angular app which formed a tree of Angular components. These components are subset of directives. Unlike directives, components always have a template and only one component can be instantiated per an element in a template.
    Let's see a simple example of Angular component
    ```typescript
    import { Component } from '@angular/core';

    @Component ({
       selector: 'my-app',
       template: ` <div>
          <h1>{{title}}</h1>
          <div>Learn Angular6 with examples</div>
       </div> `,
    })

    export class AppComponent {
       title: string = 'Welcome to Angular world';
    }
    ```

8. ### What are the differences between Component and Directive?
    In a short note, A component(@component) is a directive-with-a-template.

    Some of the major differences are mentioned in a tabular form

    | Component | Directive |
    |---- | ---------
    | To register a component we use @Component meta-data annotation  | To register directives we use @Directive meta-data annotation |
    | Components are typically used to create UI widgets| Directive is used to add behavior to an existing DOM element |
    | Component is used to break up the application into smaller components| Directive is use to design re-usable components|
    | Only one component can be present per DOM element | Many directives can be used per DOM element |
    | @View decorator or templateurl/template are mandatory | Directive doesn't use View|

9. ### What is a template?
    A template is a HTML view where you can display data by binding controls to properties of an Angular component. You can store your component's template in one of two places. You can define it inline using the template property, or you can define the template in a separate HTML file and link to it in the component metadata using the @Component decorator's templateUrl property.
    **Using inline template with template syntax,**
    ```typescript
    import { Component } from '@angular/core';

    @Component ({
       selector: 'my-app',
       template: '
          <div>
             <h1>{{title}}</h1>
             <div>Learn Angular</div>
          </div>
       '
    })

    export class AppComponent {
       title: string = 'Hello World';
    }
    ```
    **Using separate template file such as app.component.html**
    ```typescript
    import { Component } from '@angular/core';

    @Component ({
       selector: 'my-app',
       templateUrl: 'app/app.component.html'
    })

    export class AppComponent {
       title: string = 'Hello World';
    }
    ```

10. ### What is a module?

    Modules are logical boundaries in your application and the application is divided into separate modules to separate the functionality of your application.
    Lets take an example of **app.module.ts** root module declared with **@NgModule** decorator as below,
    ```typescript
    import { NgModule }      from '@angular/core';
    import { BrowserModule } from '@angular/platform-browser';
    import { AppComponent }  from './app.component';

    @NgModule ({
       imports:      [ BrowserModule ],
       declarations: [ AppComponent ],
       bootstrap:    [ AppComponent ]
    })
    export class AppModule { }
    ```
    The NgModule decorator has three options
    1. The imports option is used to import other dependent modules. The BrowserModule is required by default for any web based angular application
    2. The declarations option is used to define components in the respective module
    3. The bootstrap option tells Angular which Component to bootstrap in the application

11. ### What are lifecycle hooks available?
    Angular application goes through an entire set of processes or has a lifecycle right from its initiation to the end of the application.
    The representation of lifecycle in pictorial representation as follows,
    ![ScreenShot](images/lifecycle.png)


    The description of each lifecycle method is as below,
    1. **ngOnChanges:** When the value of a data bound property changes, then this method is called.
    2. **ngOnInit:** This is called whenever the initialization of the directive/component after Angular first displays the data-bound properties happens.
    3. **ngDoCheck:** This is for the detection and to act on changes that Angular can't or won't detect on its own.
    4. **ngAfterContentInit:** This is called in response after Angular projects external content into the component's view.
    5. **ngAfterContentChecked:** This is called in response after Angular checks the content projected into the component.
    6. **ngAfterViewInit:** This is called in response after Angular initializes the component's views and child views.
    7. **ngAfterViewChecked:** This is called in response after Angular checks the component's views and child views.
    8. **ngOnDestroy:** This is the cleanup phase just before Angular destroys the directive/component.

12. ### What is a data binding?
    Data binding is a core concept in Angular and allows to define communication between a component and the DOM, making it very easy to define interactive applications without worrying about pushing and pulling data. There are four forms of data binding(divided as 3 categories) which differ in the way the data is flowing.
    1. **From the Component to the DOM:**
    **Interpolation:** {{ value }}: Adds the value of a property from the component
    ```html
    <li>Name: {{ user.name }}</li>
    <li>Address: {{ user.address }}</li>
    ```
    **Property binding:** [property]=”value”: The value is passed from the component to the specified property or simple HTML attribute
    ```html
    <input type="email" [value]="user.email">
    ```
    2. **From the DOM to the Component:**
    **Event binding: (event)=”function”:** When a specific DOM event happens (eg.: click, change, keyup), call the specified method in the component
    ```html
    <button (click)="logout()"></button>
    ```
    3. **Two-way binding:**
    **Two-way data binding:** [(ngModel)]=”value”: Two-way data binding allows to have the data flow both ways. For example, in the below code snippet, both the email DOM input and component email property are in sync
    ```html
    <input type="email" [(ngModel)]="user.email">
    ```

13. ### What is metadata?
    Metadata is used to decorate a class so that it can configure the expected behavior of the class. The metadata is represented by decorators
    1. **Class decorators**, e.g. @Component and @NgModule
    ```typescript
    import { NgModule, Component } from '@angular/core';

    @Component({
      selector: 'my-component',
      template: '<div>Class decorator</div>',
    })
    export class MyComponent {
      constructor() {
        console.log('Hey I am a component!');
      }
    }

    @NgModule({
      imports: [],
      declarations: [],
    })
    export class MyModule {
      constructor() {
        console.log('Hey I am a module!');
      }
    }
    ```
    2. **Property decorators** Used for properties inside classes, e.g. @Input and @Output
    ```typescript
    import { Component, Input } from '@angular/core';

    @Component({
        selector: 'my-component',
        template: '<div>Property decorator</div>'
    })

    export class MyComponent {
        @Input()
        title: string;
    }
    ```
    3. **Method decorators** Used for methods inside classes, e.g. @HostListener
    ```typescript
    import { Component, HostListener } from '@angular/core';

    @Component({
        selector: 'my-component',
        template: '<div>Method decorator</div>'
    })
    export class MyComponent {
        @HostListener('click', ['$event'])
        onHostClick(event: Event) {
            // clicked, `event` available
        }
    }
    ```
    4. **Parameter decorators** Used for parameters inside class constructors, e.g. @Inject
    ```typescript
    import { Component, Inject } from '@angular/core';
    import { MyService } from './my-service';

    @Component({
        selector: 'my-component',
        template: '<div>Parameter decorator</div>'
    })
    export class MyComponent {
        constructor(@Inject(MyService) myService) {
            console.log(myService); // MyService
        }
    }
    ```

14. ### What is angular CLI?
    Angular CLI(**Command Line Interface**) is a command line interface to scaffold and build angular apps using nodejs style (commonJs) modules.
    You need to install using below npm command,
    ```
    npm install @angular/cli@latest
    ```
    Below are the list of few commands, which will come handy while creating angular projects
    1. **Creating New Project:** ng new <project-name>
    2. **Generating Components, Directives & Services:** ng generate/g <feature-name>
    The different types of commands would be,
    * ng generate class my-new-class: add a class to your application
    * ng generate component my-new-component: add a component to your application
    * ng generate directive my-new-directive: add a directive to your application
    * ng generate enum my-new-enum: add an enum to your application
    * ng generate module my-new-module: add a module to your application
    * ng generate pipe my-new-pipe: add a pipe to your application
    * ng generate service my-new-service: add a service to your application
    3. **Running the Project:** ng serve

15. ### What is the difference between constructor and ngOnInit?
    TypeScript classes has a default method called constructor which is normally used for the initialization purpose. Whereas ngOnInit method is specific to Angular, especially used to define Angular bindings. Even though constructor getting called first, it is preferred to move all of your Angular bindings to ngOnInit method.
    In order to use ngOnInit, you need to implement OnInit interface as below,
    ```typescript
    export class App implements OnInit{
      constructor(){
         //called first time before the ngOnInit()
      }

      ngOnInit(){
         //called after the constructor and called  after the first ngOnChanges()
      }
    }
    ```
16. ### What is a service?
    A service is used when a common functionality needs to be provided to various modules. Services allow for greater separation of concerns for your application and better modularity by allowing you to extract common functionality out of components.
    Let's create a repoService which can be used across components,
    ```typescript
    import { Injectable } from '@angular/core';
    import { Http } from '@angular/http';

    @Injectable() // The Injectable decorator is required for dependency injection to work
    export class RepoService{
      constructor(private http: Http){
      }

      fetchAll(){
        return this.http.get('https://api.github.com/repositories').map(res => res.json());
      }
    }
    ```
    The above service uses Http service as a dependency.

17. ### What is dependency injection in Angular?
    Dependency injection (DI), is an important application design pattern in which a class asks for dependencies from external sources rather than creating them itself. Angular comes with its own dependency injection framework for resolving dependencies( services or objects that a class needs to perform its function).So you can have your services depend on other services throughout your application.

18. ### How is Dependency Hierarchy formed?

19. ### What is the purpose of async pipe?
    The AsyncPipe subscribes to an observable or promise and returns the latest value it has emitted. When a new value is emitted, the pipe marks the component to be checked for changes.
    Let's take a time observable which continuously updates the view for every 2 seconds with the current time.
    ```typescript
    @Component({
      selector: 'async-observable-pipe',
      template: `<div><code>observable|async</code>:
           Time: {{ time | async }}</div>`
    })
    export class AsyncObservablePipeComponent {
      time = new Observable(observer =>
        setInterval(() => observer.next(new Date().toString()), 2000)
      );
    }
    ```
20. ### What is the option to choose between inline and external template file?
    You can store your component's template in one of two places. You can define it inline using the **template** property, or you can define the template in a separate HTML file and link to it in the component metadata using the **@Component** decorator's **templateUrl** property.
    The choice between inline and separate HTML is a matter of taste, circumstances, and organization policy. But normally we use inline template for small portion of code and external template file for bigger views. By default, the Angular CLI generates components with a template file. But you can override that with the below command,
    ```
    ng generate component hero -it
    ```
21. ### What is the purpose of ngFor directive?
    We use Angular ngFor directive in the template to display each item in the list. For example, here we iterate over list of users,
    ```html
    <li *ngFor="let user of users">
      {{ user }}
    </li>
    ```
    The user variable in the ngFor double-quoted instruction is a **template input variable**
22. ### What is the purpose of ngIf directive?
    Sometimes an app needs to display a view or a portion of a view only under specific circumstances. The Angular ngIf directive inserts or removes an element based on a truthy/falsy condition. Let's take an example to display a message if the user age is more than 18,
    ```html
    <p *ngIf="user.age > 18">You are not eligible for student pass!</p>
    ```
    **Note:** Angular isn't showing and hiding the message. It is adding and removing the paragraph element from the DOM. That improves performance, especially in the larger projects with many data bindings.

23. ### What happens if you use script tag inside template?

    Angular recognizes the value as unsafe and automatically sanitizes it, which removes the **<script>** tag but keeps safe content such as the text content of the <script> tag. This way it eliminates the risk of script injection attacks. If you still use it then it will be ignored and a warning appears in the browser console.
    Let's take an example of innerHtml property binding which causes XSS vulnerability,
    ```typescript
    export class InnerHtmlBindingComponent {
      // For example, a user/attacker-controlled value from a URL.
      htmlSnippet = 'Template <script>alert("0wned")</script> <b>Syntax</b>';
    }
    ```

24. ### What is interpolation?

    Interpolation is a special syntax that Angular converts into property binding. It’s a convenient alternative to property binding. It is represented by double curly braces({{}}). The text between the braces is often the name of a component property. Angular replaces that name with the string value of the corresponding component property.
    Let's take an example,
    ```html
    <h3>
      {{title}}
      <img src="{{url}}" style="height:30px">
    </h3>
    ```
    In the example above, Angular evaluates the title and url properties and fills in the blanks, first displaying a bold application title and then a URL.

25. ### What are template expressions?
    A template expression produces a value similar to any Javascript expression. Angular executes the expression and assigns it to a property of a binding target; the target might be an HTML element, a component, or a directive. In the property binding, a template expression appears in quotes to the right of the = symbol as in [property]="expression".
    In interpolation syntax, the template expression is surrounded by double curly braces. For example, in the below interpolation, the template expression is {{username}},
    ```html
    <h3>{{username}}, welcome to Angular</h3>
    ```
    The below javascript expressions are prohibited in template expression
    1. assignments (=, +=, -=, ...)
    2. new
    3. chaining expressions with ; or ,
    4. increment and decrement operators (++ and --)
    ----------------------------------
26. ### What are template statements?
    A template statement responds to an event raised by a binding target such as an element, component, or directive. The template statements appear in quotes to the right of the = symbol like **(event)="statement"**. Let's take an example of button click event's statement
    ```html
    <button (click)="editProfile()">Edit Profile</button>
    ```
    In the above expression, editProfile is a template statement. The below JavaScript syntax expressions are not allowed.
    1. new
    2. increment and decrement operators, ++ and --
    3. operator assignment, such as += and -=
    4. the bitwise operators | and &
    5. the template expression operators
    --------------------------------------
27. ### How do you categorize data binding types?

     Binding types can be grouped into three categories distinguished by the direction of data flow. They are listed as below,
     1. From the source-to-view
     2. From view-to-source
     3. View-to-source-to-view

     The possible binding syntax can be tabularized as below,

     | Data direction | Syntax | Type |
     |---- | ---------
     | From the source-to-view(One-way)  | 1. {{expression}} 2. [target]="expression" 3. bind-target="expression" | Interpolation, Property, Attribute, Class, Style|
     | From view-to-source(One-way) | 1. (target)="statement" 2. on-target="statement" | Event |
     | View-to-source-to-view(Two-way)| 1. [(target)]="expression" 2. bindon-target="expression"| Two-way |







