# Angular

## Homepage

- <a target="_blank" href="https://angular.io/">Angular: Features, Docs, Resources, Events</a>
- <a target="_blank" href="https://material.angular.io">Angular: Materials</a>

## Angular CLI

- <a target="_blank" href="https://cli.angular.io/">Angular CLI</a>
- <a target="\_blank" href="https://medium.com/@tomastrajan/6-best-practices-pro-tips-for-angular-cli-better-developer-experience-7b328bc9db81">Medium: 6 Best Practices and Pro Tips when using Angular CLI</a>

## Best Practices

- <a target="_blank" href="https://blog.angular.io/version-6-of-angular-now-available-cc56b0efa7a4">Medium: Version 6 of Angular Now Available</a>

## Libraries

- <a href="https://rxjs-dev.firebaseapp.com/" target="_blank">RxJS - Reactive Extensions Library for JavaScript</a>
- <a href="http://rxmarbles.com/" target="_blank">RxJS Marbles</a>

## Components

- <a href="https://www.ag-grid.com/" target="_blank">agGrid</a>
- <a href="https://www.jqwidgets.com/" target="_blank">jQWidgets</a>
- <a href="http://valor-software.com/ngx-bootstrap/#/" target="_blank">NGX-Bootstrap</a>
- <a href="https://www.primefaces.org/primeng/#/" target="_blank">PrimeNG</a>

## How to ..

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
