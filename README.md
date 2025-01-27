# Django_Rest_Framework
| Approach                         | Description                                                                                   | When to Use                                                                 |
|----------------------------------|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| Dynamic Actions in a Single View | Handle multiple actions in one view using a parameter (e.g., action).                         | Small applications with simple forms and limited actions.                  |
| Separate Views for Each Action   | Create separate views for each action (e.g., register, signin, logout).                       | Medium to large applications with complex logic for each action.           |
| Hybrid Approach                  | Combine Django templates for server-side rendering with DRF APIs.                            | Monolithic applications with tightly coupled backend and frontend.         |
| Advanced Renderer Usage          | Customize response formats using DRF renderers (e.g., JSON, HTML, plain text).               | When you need to support multiple response formats.                        |
| Redirection and HTML Rendering   | Use redirect and TemplateHTMLRenderer to navigate and render HTML pages.                     | When you need to redirect users and render HTML templates.                 |

---

**Decision Tree for Choosing an Approach**

- **Is your frontend completely separate (e.g., React, Angular, Vue.js)?**
  - Yes → Use API-Only (No Templates).
  - No → Proceed to the next question.
  
- **Do you need server-rendered HTML pages?**
  - Yes → Proceed to the next question.
  - No → Use API-Only (No Templates).

- **Do you need to handle multiple actions in one view?**
  - Yes → Use Dynamic Actions in a Single View.
  - No → Use Separate Views for Each Action.

- **Do you need to support multiple response formats (e.g., JSON, HTML)?**
  - Yes → Use Advanced Renderer Usage.
  - No → Use Hybrid Approach.

- **Do you need to redirect users and render HTML templates?**
  - Yes → Use Redirection and HTML Rendering.
  - No → Use Hybrid Approach.

---

**Deserialization**  
We use deserialization when performing create, update, and delete actions.  
For this flow:
1. Extract data from the request body.
2. As it is in stream (in bytes), parse it into Python data through a JSON parser.
3. Pass this Python data to the serializer.
4. After validation, save it and display a success message ("Data created successfully").  

The serializer works for both serialization (getting the model instance, passing it to the serializer, converting it to JSON through the JSON renderer, and sending it to the frontend, mostly for data reading) and deserialization (create, update, delete actions).

---

**Field Level Validation**

```python
def validate_fieldname(self):
    # Condition
# Django Rest Framework (DRF) Implementation Approaches

DRF can be implemented in various ways depending on your project's requirements. Below is a breakdown of the most common approaches, their use cases, and a decision tree to help you choose the best approach.


## Table of DRF Implementation Approaches

| Approach | Description | When to Use |
|---|---|---|
| API-Only (No Templates) | DRF is used solely for building RESTful APIs. No Django templates are used. | When the frontend is completely separate (e.g., React, Angular, Vue.js). |
| API + Templates (Admin/Simple UI) | DRF provides APIs, and Django templates are used for admin or simple UIs. | When you need a simple frontend or admin interface alongside APIs. |
| Hybrid Approach (API + Templates) | DRF provides APIs, and Django templates are used for rendering the frontend. | When you want a monolithic app with server-rendered templates and APIs. |
| API + Templates for Forms | DRF handles APIs, and Django templates are used for form rendering/handling. | When you need to render and process forms using Django templates. |
| API + Templates for SSR | DRF provides APIs, and Django templates are used for server-side rendering. | When you need to render dynamic HTML pages on the server. |
| API + Templates for Auth | DRF handles APIs, and Django templates are used for auth pages (login, etc.). | When you need to use Django's built-in auth system alongside APIs. |
| API + Templates for Docs | DRF provides APIs, and Django templates are used for custom API documentation. | When you need to create custom API documentation pages. |
| API + Templates for Testing | DRF provides APIs, and Django templates are used for testing/debugging. | During development for testing and debugging purposes. |


## **Decision Tree for Choosing an Approach**

1. **Is your frontend completely separate (e.g., React, Angular, Vue.js)?**

- **Yes** → Use **API-Only (No Templates)**.

- **No** → Proceed to the next question.

- **Do you need server-rendered HTML pages?**

- **Yes** → Proceed to the next question.

- **No** → Use **API-Only (No Templates)**.

- **Do you need to render forms using Django templates?**

- **Yes** → Use **API + Templates for Forms**.

- **No** → Proceed to the next question.

- **Do you need to render dynamic HTML pages on the server?**

- **Yes** → Use **API + Templates for SSR**.

- **No** → Proceed to the next question.

- **Do you need to use Django's built-in authentication system?**

- **Yes** → Use **API + Templates for Auth**.

- **No** → Proceed to the next question.

- **Do you need custom API documentation pages?**

- **Yes** → Use **API + Templates for Docs**.

- **No** → Proceed to the next question.

- **Do you need testing/debugging pages during development?**

- **Yes** → Use **API + Templates for Testing**.

- **No** → Use **Hybrid Approach (API + Templates)**.

**Let’s consolidate all the concepts and approaches you’ve mentioned into a comprehensive guide that covers:**

1. **Dynamic Actions in a Single View**.

2. **Separate Views for Each Action**.

3. **Hybrid Approach (Combining Templates and APIs)**.

4. **Advanced Renderer Usage in DRF**.

5. **Redirection and HTML Rendering in DRF**.

This guide will provide a clear understanding of how to implement these approaches in Django Rest Framework (DRF) and when to use each one.




## **6. Combining All Approaches**

You can combine the above approaches to build a flexible and powerful application. For example:

- Use **separate views** for each action.

- Use **templates** for server-side rendering.

- Use **APIs** for dynamic functionality.

- Use **renderers** to support multiple response formats.

- Use **redirection** to navigate between pages.

### **Example Workflow**

1. **User visits the home page** (`/`):

- Render an HTML template using `TemplateHTMLRenderer`.

- **User submits a form**:

- Handle the form submission in a DRF view.

- Use `redirect` to navigate to another page.

- **User requests data in JSON format**:

- Use `JSONRenderer` to return a JSON response.

- **User requests data in plain text format**:

- Use a custom `PlainTextRenderer` to return a plain text response.


## **Summary of Approaches**

| Approach | Description | When to Use |
|---|---|---|
| Dynamic Actions in a Single View | Handle multiple actions in one view using a parameter (e.g., action). | Small applications with simple forms and limited actions. |
| Separate Views for Each Action | Create separate views for each action (e.g., register, signin, logout). | Medium to large applications with complex logic for each action. |
| Hybrid Approach | Combine Django templates for server-side rendering with DRF APIs. | Monolithic applications with tightly coupled backend and frontend. |
| Advanced Renderer Usage | Customize response formats using DRF renderers (e.g., JSON, HTML, plain text). | When you need to support multiple response formats. |
| Redirection and HTML Rendering | Use redirect and TemplateHTMLRenderer to navigate and render HTML pages. | When you need to redirect users and render HTML templates. |


## **Decision Tree for Choosing an Approach**

1. **Is your frontend completely separate (e.g., React, Angular, Vue.js)?**

- **Yes** → Use **API-Only (No Templates)**.

- **No** → Proceed to the next question.

- **Do you need server-rendered HTML pages?**

- **Yes** → Proceed to the next question.

- **No** → Use **API-Only (No Templates)**.

- **Do you need to handle multiple actions in one view?**

- **Yes** → Use **Dynamic Actions in a Single View**.

- **No** → Use **Separate Views for Each Action**.

- **Do you need to support multiple response formats (e.g., JSON, HTML)?**

- **Yes** → Use **Advanced Renderer Usage**.

- **No** → Use **Hybrid Approach**.

- **Do you need to redirect users and render HTML templates?**

- **Yes** → Use **Redirection and HTML Rendering**.

- **No** → Use **Hybrid Approach**.

**Deserialization we use when to  do these →Create,update and delete**

For this flow

Extract data from request body

As it is in stream mean in bytes so parse it in python data through JSON parser and then this python data pass to the serializer and after validation will be saved and then simple show the message of data created successfully

Here serializer working for both serialization (which get the model instance and the pass to the serializer and the convert to json through JSON renderer and then send to the front end and its mostly for just data reading)and deserialization involve create, update delete actions

**Field level validation** 

Def validate_fieldname(self):

Condition

Object level mean validation on multiple fields

Def validate(self,data):

name=data.get("name")

Validators

These are used when we have to do the most repeated validation

Def functionname():

Condition

name=serializer.charfield(others_params,validators[functionname])

**Modelform/model serializer**

These are similar mean we don't need to create the fields but automatically creates and validators applies on them,nd automatically do for creates, update

As we were creating firstly class by using serializer.serializer but now we will create by using serializer.modelserializer

Now just use the meta class and write the fields name which you are required ,if we want to validate a specific field then just write above the meta class as

Name=serializer.charfield(params,validators[functionname]) also here in this field you can make it read only =true

And if for multiple fields you want to read only then just write under the meta class

Similar validation for one field using function under the meta class

Similar for object level validation

Validators on specific field if repeatedly need the validation using validators inside the field

**View** mostly we say to functions, but** APIview **is for classes which provides the requests methods as per request is hit i.e. get,post and all other methods and we have to define all these methods in this sub Apiview class and then this class will serve the methods as per request is hit,and it has a lot of methods i.e. query_set and other so see documentation for this

**Mixin **it provides all the common behavior like CRUD operations on table its provides the functionalities so just use them,mean we don't need to write the queryset codes ,validate and save this is automatically handled by these classes GenericApiview and modelmixin as we have to write again and again the code of CRUD in views but by using these classes we don't need further more

Also these classes use request methods along with returning the methods respect to the applied mixin,we can shorten the code further as by keeping in the same class i.e. the classes which don't need pk will be in the one class which will inherit the genericapiview,createmodelmixin,listmodelmixin and return the rlevant methods and those group which requires pk will be in the same class other group

**Difference between Apiview **as these provides the requests methods, **genericapiview classes** provides the automatically handled the repeated pattern queryset operations of CRUD on model instance, along with the mixins, while **concreteApiView provides** the same behavior as genericapiview classes but these provides the more customization separately like for Creation,updation deletion etc for these provides the built-in classes like listapiview,createapiview and others etc.Also they provide the classes that handled the combination like for Creation and listening it provides createlistapiview, updateretriveapiview etc

Mean concrete Apiview extends both genericapiview and mixinmodelview and no need both of them anymore when we have the concrete Apiview as it uses the concepts of both of these

**Apiview and viewset** the difference is that viewset provides the action like create,list, CRUD etc instead of methods in Apiview post,get etc, and we can create the CRUD logic at once in the viewset class which will handle automatically CRUD operations on table instances ,router is used for such things which handle the CRUD operations under the sme route including pk etc . The advantage of this class is that repeated set of view logic can be handled under the sme class , router mean no need to define separate URL for those repeated set of view logic

**Modelviewset** is the similar to the above viewset but it's handle the CRUD operations on the instance automatically no need to write the viewset methods separately as above in the viewset and it overrides the methods of apigenericview and uses the concepts of mixin behind the scene

**Authentications:**

**2-Session authentication**

**3-token authentication**

**4-custom authentication**

**5-jwt authentication**

**Authentications:**

**1-Basic authentication**(it uses HTTP authentication which uses user's username and password for authentication, it's mostly do for the testing purposes but for production then use this over https and re-request user's username and password.

**These permission classes are isauthenticated,allowany,isadmin, Djangomodelpermissiononly, isauthenticatedreadonly,djandomodelpermissionorannotatedonly**

If view are class based then these classes i.e. authentication and permission will be used inside the class but for the function base view these classes will be as decorators above the function ,this authentication and permission was to the specific class or function but what if we have to apply globally authentication and permission to all the classes or functions then add these authentication and permission inside the setting.py file, but what if we don't want to apply the authentication and permission to some class as we have set globally authentication and permission so to do this simple write inside the class or function and it will overwrite the global authentication and permission,also we can set the multiple authentication and permission in the square bracket when we write them there in the function or class

)

**2-Session authentication**(uses Django default session backend for authentication  ,mean the session currently in which user is using the website is authnticated then session provides these things request.user which is the Django instance and request.auth None,if we use ajax session authentication then make sure to use the secure csrf token methods like post,patch,update etc,also for Djangomodelpermissions we have to explicitly assign the permission from admin panel to perform the CRUD operations.

)

**Custom Permission** we have to override the base permission by using either or both of the methods i.e. **has_permission,has_permision_object()**,these methods will be defined the inside the class which will inherit the base permission and now use this inside the api class along the authentication, also there are third parties permission in drf which provides the permission 

**3-token authentication**

**4-custom authentication** (to apply this inherit from base authentication class and override the authenticate method which return tuple as i.e.(user,auth) and then use this custom inside the API class inside the authentication in bracket 

**5-jwt authentication**

**Token authentication**:it is token base http authentication ,its best option when there is desktop and mobile app and to use it configure it in installed app and then make sure migrate as it provides db migrations,if authentication is successful the it provides request.user which is Django instance and request.auth which is token.auth instance ,to use it in production then use https,also to create token for this use Django admin, python manage.py command i.e.

Python manage.py drf_create_toke <username>,by using signal and exposing end points

**Relationship in serializer**, when we make serializer from** model.serializer,there is also another hyperlinkedmodelserializer which is similar to modelserializer** which have relationship with each other on the relatedname param so then this relatedname param will be used also in serializer to access the relationship fields, but this param will return id but what if we want the value then simply in serializer class before meta crete the field and inside it many=True and readonly=True and then use this field inside the feilds to access it

Similar we also create the field related to **primarykey,hyperlinked,slugfield, hyperlinkedidentity fields etc**

Also we can do nested serializer mean when we have to show all the details of other serializer in this one ,so simply write down that serializer and and add this in the fields as a field

**: Filter**

In drf we can override the get_query method to get the results on the filter base ,for current user we can use the request.user this return the current user ,we can also use the Djangofilterbackend for highly customizably filtering ,to use it frst install and set in installed app in setting file for further read the documenation of this,for globally set it in rest_framewrok and to use for per view using genericapiview

SearchFilter it supports single query parameter base search ,to ise it include search_field in in your view ,

OrderingFilter for ordering the results

**Pagination** 

Globally in setting file set it in rest_framework and which class you have to use write it from below described 3 classes

For per view, you can set the pagination class on per view along with the page size mean to show number of records per page

**1-pagenumberpagination**,we can override it by inheritting it as a subclass and then use that in the view, paginationqury_params mean the pagination means pages numbering,if we want to decide the page size by client then we can do page_size_query_params

**2-limitoffpagination**

**3-cursor pagination**

**Throttling** mean to limit the rate of api hitting 

And we can set it in globally in setting file for both annotated user and authorizeduser

3 classes used for per view

As annonthrotleclass,userthrotleclass,scopedthrotleclass,we can customize the these classes for per view use


