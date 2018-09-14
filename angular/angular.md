# Angular

## Homepage

- <a target="_blank" href="https://angular.io/">Angular: Features, Docs, Resources, Events</a>
- <a target="_blank" href="https://material.angular.io">Angular: Materials</a>

## Angular CLI

- <a target="_blank" href="https://cli.angular.io/">Angular CLI</a>

## Best Practices

- <a target="_blank" href="https://alligator.io/angular/">alligator.io: Angular</a>

## Libraries

- <a href="https://github.com/ngrx/platform" target="_blank">@ngrx (Reactive libraries for Angular)</a>
- <a href="https://gist.github.com/btroncone/a6e4347326749f938510" target="_blank">Comprehensive Introduction to @ngrx/store</a>
- <a href="https://rxjs-dev.firebaseapp.com/" target="_blank">RxJS - Reactive Extensions Library for JavaScript</a>
- <a href="http://rxmarbles.com/" target="_blank">RxJS Marbles</a>
- <a href="https://github.com/typicode/json-server" target="_blank">JSON Server</a>
- <a href="https://jsonplaceholder.typicode.com/" target="_blank">JSONPlaceholder</a>
- <a href="https://www.mocky.io/" target="_blank">mocky.io</a>
- <a href="https://www.mocky.io/v2/58de0960280000a31d9e4bc1" target="_blank">mocky.io: sample</a>

## Components

- <a href="https://www.ag-grid.com/" target="_blank">agGrid (UI)</a>
- <a href="https://github.com/FuelInteractive/fuel-ui" target="_blank">Fuel-UI (UI)</a>
- <a href="https://github.com/ng-lightning/ng-lightning" target="_blank">ng-lightning (UI)</a>
- <a href="https://onsen.io/" target="_blank">Onsen UI (UI)</a>
- <a href="https://ng-semantic.herokuapp.com/#/" target="_blank">ngSemantic (UI)</a>
- <a href="https://www.jqwidgets.com/" target="_blank">jQWidgets (UI)</a>
- <a href="https://material.angular.io/" target="_blank">Angular Material (UI)</a>
- <a href="http://valor-software.com/ngx-bootstrap/#/" target="_blank">NGX-Bootstrap (UI)</a>
- <a href="https://www.primefaces.org/primeng/#/" target="_blank">PrimeNG (UI)</a>
- <a href="https://github.com/valor-software/ng2-dragula" target="_blank">Dragula (drag'n'drop)</a>

## How to ..

### Medium

- <a target="_blank" href="https://blog.angular.io/version-6-of-angular-now-available-cc56b0efa7a4">Medium: Version 6 of Angular Now Available</a>
- <a target="\_blank" href="https://medium.com/@tomastrajan/6-best-practices-pro-tips-for-angular-cli-better-developer-experience-7b328bc9db81">Medium: 6 Best Practices and Pro Tips when using Angular CLI</a>
- <a href="https://medium.com/@ladyleet/popups-modals-and-navigation-using-angular-material-2-components-in-your-angular-2-project-faf510dbcdee" target="_blank">Popups, Modals, and Navigation — Using Angular Material (2) Components in your Angular (2) Project</a>
- <a href="https://medium.com/front-end-hacking/a-guide-to-debugging-angular-applications-5a36bd88b4cf" target="_blank">A Guide To Debugging Angular Applications</a>
- <a href="https://blog.angularindepth.com/everything-you-need-to-know-about-debugging-angular-applications-d308ed8a51b4" target="_blank">Everything you need to know about debugging Angular applications</a>
- <a href="https://medium.com/@zalmoxis/using-redux-devtools-in-production-4c5b56c5600f" target="_blank">Using Redux DevTools in production</a>
- <a href="https://itnext.io/ngrx-best-practices-for-enterprise-angular-applications-6f00bcdf36d7" target="_blank">NgRx — Best Practices for Enterprise Angular Applications</a>
- <a href="https://medium.com/ngrx/introducing-ngrx-entity-598176456e15" target="_blank">Introducing @ngrx/entity</a>
- <a href="https://medium.com/@amcdnl/global-error-handling-with-angular2-6b992bdfb59c" target="_blank">Global Error Handling with Angular2+</a>
- <a href="https://blog.bitsrc.io/11-angular-component-libraries-you-should-know-in-2018-e9f9c9d544ff" target="_blank">11 Angular Component Libraries You Should Know In 2018</a>

### vehicle.service.ts: define return type

Return type: <code>Vehicle[]</code>

```javascript
import { HttpClient } from '@angular/common/http';
import { Injectable } from '@angular/core';

import { Observable } from 'rxjs';
import { tap, map } from 'rxjs/operators';

import { Vehicle } from './../models/vehicle.model';

@Injectable({
  providedIn: 'root'
})
export class VehicleService {
  constructor(private _http: HttpClient) {}

  /**
   * Find all vehicles.
   * @returns {Vehicle[]}  -  A list of vehicles.
   */
  public findAll(): Observable<Vehicle[]> {
    return this._http.get<Vehicle[]>('http://localhost:3000/vehicles');
  }
}
```

### tsconfig.json: own path definitions

To use of the @-annotations for imports within own project modules.

```json
...
"paths": {
  "@observableWeather/*": ["app/with-observables/*"],
  "@currentWeather/*": ["app/current/*"],
  "@app/*": ["app/*"],
  "@env/*": ["environments/*"]
}
...
```
