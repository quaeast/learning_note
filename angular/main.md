# Angular

## Angular CLI

### Bootstrap

```bash
npm install -g @angular/cli

ng new my-dream-app

cd mu-dream-app

ng serve
```

### Common commands

```
ng generate component components/my-component

ng generate service services/my-service

ng add @angular/material

ng build --prod
```

## Directives

There are three categories of directives: attribute directives, structural directives, and components.

```
*ngIf="!stocks"

*ngFor="let stock of stocks"

# adding css class to this element
[ngClass]="{increase: isPositive(), decrease: isNegative()}"

# used in input elements of form, bind input content to JS object，two-way bind
[(ngModel)]="stock"
```