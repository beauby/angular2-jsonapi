# Architecture

This is just a proposal of a potential set of classes / services and their responsibilities and what APIs they may have.

## Top-Level Objects

<table>
  <thead>
    <tr><th style='width: 120px'>Object</th><th>Description / Responsibility</th><th>Example APIs</th>
  </thead>
  <tbody>
    <tr>
      <td>Model</td><td>defines the attributes and relationships for resources </td>
      <td>
        - save()<br>
        - destroy()<br>
        - delete()<br>
        - rollbackAttributes()<br>
        - hasDirtyAttributes()<br>
        - errors<br>
        - serialize()<br>
      </td>
    </tr>
    <tr>
      <td>Store</td>
      <td>
        - retrieves models from the locale storage<br>
        - retrieves models from the server<br>
        - performs CRUD on any resource
      </td>
      <td>
        - createRecord(type, params)<br>
        - findRecord(type, options)<br>
        - peekRecord(type, id)<br>
        - findAll(type)<br>
        - peekAll(type)<br>
        - query(type, params)<br>
        - queryRecord(type, params)<br>
      </td>
    </tr>  
    <tr>
      <td>- Resource</td><td>a json api document? - not sure if this needs to be an object</td>
    </tr>
    <tr>
      <td>Serializer</td>
      <td>
        - allows customizing of the the raw json sent out to the server<br>
        - allows customizing of the raw json retrieved from the server
      </td>
      <td>
        - serializeForServer(...)<br>
        - normalizeFromServer(...)
      </td>
    </tr>

    <tr>
      <td>Errors</td><td>represents json-api formatted error data</td>
      <td>
      </td>
    </tr>

    <tr>
      <td></td><td></td>
      <td>
      </td>
    </tr>

  </tbody>
</table>


## Non-Public Objects

 - HasManyRelationship
 - BelongsToRelationship



## Ideas inspired by:

 - [EmberData](http://emberjs.com/api/data/)
   - [Defining Models](https://guides.emberjs.com/v2.5.0/models/defining-models/)
   - [Finding Records](https://guides.emberjs.com/v2.5.0/models/finding-records/)
   - [Create, Update, Delete](https://guides.emberjs.com/v2.5.0/models/creating-updating-and-deleting-records/)
   - [Customizing Serializers](https://guides.emberjs.com/v2.5.0/models/customizing-serializers/)
