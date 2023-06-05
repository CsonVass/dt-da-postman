## Tests
Tests can be written in javascript in the `Tests` page.

![img](../img/test-code.png)

Sample test for `http://localhost:5000/hosts` API endpoint
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response body is not empty", function () {
    pm.response.to.be.ok;
    pm.response.to.have.jsonBody;
});

pm.test("Response contains expected data", function () {
    var responseBody = pm.response.json();

    pm.expect(responseBody).to.be.an('array');
    pm.expect(responseBody.length).to.be.greaterThan(0);
    pm.expect(responseBody[0]).to.have.property('id');
    pm.expect(responseBody[0]).to.have.property('hostname');
});
```

Tests are ran with the collections and they show the results.

![img](../img/test-run.png)

They can also be executed automatically 

![img](../img/automate-run.png)

![img](../img/automate-config.png)

and also with CLI. 
Postman has long been known for its command-line interface (CLI) tool, Newman. However, in recent times, Postman CLI has emerged as a robust alternative, offering enhanced security features and expanded functionality.

|                                                                                                        | Newman      | Postman CLI       |
| ------------------------------------------------------------------------------------------------------ | ----------- | ----------------- |
| Release date                                                                                           | 2014        | 2022              |
| Source Control                                                                                         | Open source | Closed Source     |
| Install                                                                                                | npm         | platform specific |
| Signed by Postman                                                                                      | No          | Yes               |
| Results shown in Postman app                                                                           | No          | Yes               |
| Additional Security                                                                                    |             | More              |
| API key                                                                                                | No          | Yes               |
| export collections, environments, and global variables before completing the execution of a collection | Yes         | No                |

More: https://blog.postman.com/postman-cli-vs-newman/



While both Newman and the Postman CLI offer similar core functionality, they have distinct features and appearances. Despite their differences, they both serve as command-line tools for working with Postman collections and running API tests. Users who are familiar with Newman will find the Postman CLI interface to be familiar and intuitive, making it easier to transition between the two tools.

**Newman**

![img](../img/newman.png)

**Postman CLI**

![img](../img/automate-cli.png)

![img](../img/postman-cli-first.png)

### Mocking

When the server-side implementation is not yet ready, but the client-side requires access to certain endpoints, configuring a mock server can be a viable solution. By setting up a mock server, you can define specific responses for particular requests, allowing the client-side to receive the expected results.

A mock server replicates the behavior of the actual server by intercepting API requests and returning predefined responses. This enables the client-side development to progress smoothly, even in the absence of a fully functional backend.

![img](../img/mock.png)

![img](../img/mock-setup.png)

Let's consider an example that illustrates the distinction between using our sample project and a mock server. In our sample project, the delete function behaves differently depending on whether the ID exists or not. Specifically, for non-existing IDs, it returns a 404 response, whereas for existing IDs, it returns a 204 response. Due to this variation in the expected outcomes, our test for the delete function lacks determinism.

![img](../img/postman-cli.png)

When utilizing a mock server, the actual backend logic is not executed, resulting in the same response being obtained consistently for every run. The mock server provides predetermined responses, independent of the real backend's behavior.

![img](../img/postman-cli-first.png)