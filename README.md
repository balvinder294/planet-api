# Planet-Api APP With Angular6 Client and ExpressJs Server 

## Steps for adding new Api to planet-server App

1. Create a folder in server > api > controller with any name. We have examples folder here.

2. Next create two files controller.js and router.js, where controller is used for business logic and router.js for setting *Rest* Api endpoints for crud methods.

3. Create a service file inside folder server > api > services. This service file contains crud methods.

4. Now import router as name like *examplesRouter* to routes.js.

4. Now add *examplesRouter* to default routes like

    `app.use('/api/v1/examples', examplesRouter);`

5. Now add these Api to Api.yaml like

```

paths:
  /examples:
    get:
      tags:
        - Examples
      description: Fetch all examples
      responses:
        200:
          description: Returns all examples
    post:
      tags:
        - Examples
      description: Create a new example
      parameters:
        - name: example
          in: body
          description: an example
          required: true
          schema: 
            $ref: "#/definitions/ExampleBody"
      responses:
        200:
          description: Returns all examples

  /examples/{id}:
    get:
      tags:
        - Examples
      parameters:
        - name: id
          in: path
          required: true
          description: The id of the example to retrieve
          type: integer
      responses:
        200:
          description: Return the example with the specified id
        404:
          description: Example not found

```

7. Add definitions for expected data values

```
definitions:
  ExampleBody:
    type: object
    title: example
    required:
      - name
    properties:
      name:
        type: string
        example: no_stress
```

8. Don't forget to add tags , they group the Api for controllers like *Examples* tag will group all Api's of Examples Crud operation.