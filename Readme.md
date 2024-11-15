Steps to apply add a set of custom templates to Dev Spaces dashboard
======================================================================
1. Clone this git repository
   
2. The file `custom-template.json` contains one sample for .NET 6.0.
   
3. Edit the custom-template.json to include/add other required templates.
   
4. Update the following in each template in this JSON file
   
   a. URL should point to git repo that contains the starter code + devfile
   
   b. displayName, description, tags should be updated to refer to relevant tech stack
   
   c. icon.base64data should contain the base64 representation of the image that is required.
   Use base64 cli to do the conversion. For example, `base64 -i png-transparent-net-core-thumbnail.png > output_base64.txt` and copy the base64 value
   
6. Create a configmap in the namespace where Dev Spaces is deployed and label it accordingly.
```
oc create configmap mas-custom-template --from-file=custom-template.json -n <namespace of Dev Spaces>

oc label configmap mas-custom-template app.kubernetes.io/part-of=che.eclipse.org app.kubernetes.io/component=getting-started-samples -n <namespace of Dev Spaces>
```
