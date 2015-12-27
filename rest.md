#RESTFUL DESIGN PATTERN

        REST play the "Procedure" aspect and define a small number of "action" based on existing HTTP Methods. As we discussed above, HTTP GET is used to get a representation of the resource. To modify a resource, REST use HTTP PUT with the new representation embedded inside the HTTP Body. To delete a resource, REST use HTTP DELETE. To get metadata of a resource, REST use HTTP HEAD. 
  
   SOAP : The Remote Procedure Call Model

 	Under this model, "Service" is structured as some "Procedure" exposed by the system.SOAP is used to define how to encode the procedure call into an XML string.
        "Service" in the SOA is organized as large number of "Resources". Each resource will have a URI that make it globally identifiable. A resource is represented by some format of "Representation" which is typically extracted by an idempotent HTTP GET. The representation may embed other URI which refers to other resources. This emulates an HTML link between web pages and provide a powerful way for the client to discover other services by traversing its links.

   REST: The Resource Oriented Model

	REST is modeled around a large number of "Resources" which "link" among each other. As a significant difference with WS*, REST raises the importance of "Resources" as well as its "Linkage", on the other hand, it push down the importance of "Procedures".

        REST allows any "Procedure" (which has a side effect) to use HTTP POST. Effectively, REST categorize the operations by its nature and associate well-defined semantics with these categories (ie: GET for read-only, PUT for update, DELETE for remove, all above are idempotent) while provide an extension mechanism for application-specific operations.

   URI Naming Convention:

	"Factory Resource" which create other resources. Factory resource typically represents the "type" of resources. Factory resource usually have a static, well-known URI, which is suffixed by a plural form of the resource type. Some examples are ...

             http://xyz.com/books

        "Resource Instance", which are created by the "Factory Resource" usually represents an instance of that resource type. "Resource instances" typically have a limited life span. Their URI typically contains some unique identifier so that the corresponding instance of the resource can be located. Some examples are ...

             http://xyz.com/books/4545

        "Dependent Resource" are typically created and owned by an existing resource during part of its life cycle. Therefore "dependent resource" has an implicit life-cycle dependency on its owning parent.
When a parent resource is deleted, all the dependent resource it owns will be deleted automatically. Dependent resource use an URI which has prefix of its parent resource URI. Some examples are

             http://xyz.com/books/4545/tableofcontent

        "Transaction Resource" to immediately create a "Transaction Resource" to return back to the client. While the actual processing happens asynchronously in the background, the client at any time, can poll the "Transaction Resource" for the latest processing status.

   Restful API Design:

       Relationships between resources are expressed as hyperlinks in the representation of the resource. This is one of the fundamental principles of RESTful API design. Resources also respond to a very limited set of operations (usually just 4), which is a second principle of the RESTful architectural style.

       When transforming objects from the application data model to RESTful resources, you may find it useful to define two utility functions:

         to_resource():
                        This function is assumed to take an object from the application data model, and convert it into a resource.

         from_resource():
                        This function is assumed to take a resource, and translate it into an object in the application data model.

        
