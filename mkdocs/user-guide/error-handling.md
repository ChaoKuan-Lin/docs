# Error Handling

All errors use **Respond Status Code** to identify and use **Responding message** to display the error messages.

| Code | Response Status       | Description                                 |
| :-:  | :-:                   | :-                                          |
| 400  | Bad Request           | Request parameters are incorrect or invalid |
| 401  | Unauthorized          | Incorrect authentication                    |
| 403  | Forbidden             | The API cannot be used                      |
| 404  | Not Found             | Resource cannot be found                    |
| 409  | Conflict              | Resource already exists                     |
| 500  | Internal Server Error | Please [contact us](mailto:us@mobagel.com)  |

> More information about [response status code](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)