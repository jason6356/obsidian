### The API Endpoint for the SAINOFORCE EHRM System

> https://demo2020.365hr.com.my:8091/api/Employee/GetEmployeeStatus


#### Parameters Needed

|Parameter | Values |
|-|-|
| Name | Name of the Employee|
| IC | Ic of the Employee|

This API is used to fetch the actual data from the EHRM System from the company
however we do not have the actual name and ic that we need to get a good response from this api


```ts
import { Injectable } from '@angular/core';
import { HttpClient, HttpParams } from '@angular/common/http';
import { AgentStatus } from '../enums/agent-status.enum';
import { Observable, of } from 'rxjs';
import { catchError, switchMap, map, tap } from 'rxjs/operators';

@Injectable({
  providedIn: 'root'
})
export class SainoService {
    constructor(private http: HttpClient) { }
    
    getEmployeeStatus(name:string, ic:string): Observable<any> {
      name = name.replace(/ /g, '%20');
      return this.http.get<any>(`https://demo2020.365hr.com.my:8091/api/Employee/GetEmployeeStatus?Name=${name}&IC=${ic}`)
        .pipe(
          catchError(this.handleError<any[]>('getEmployeeStatus', []))
        )
    }
  
    private handleError<T>(operation = 'operation', result?: T) {
        return (error: any): Observable<T> => {
          console.error(`${operation} failed: ${error.message}`);
          // Prevent application from completely erroring out.
          return of(result as T);
        };
      }  

}

```

This is the service component they use to integrate with the EHRM system, however by missing the information we needed, we cant actually use this API

The reason of this implementation is because that they are trying to set some authorization for the Issuer and Verifier so that they can issue and verify the credential offer from the Holder
