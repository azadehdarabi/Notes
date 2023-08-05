
`<label>` must attach to something

`changelist_view` method:
everything in admin panel -> 
`response = super(BaseAdmin, self).changelist_view(request, extra_context)`


```python
def changelist_view(self, request, extra_context=None):  
    response = super(BaseAdmin, self).changelist_view(request, extra_context)  
    model_full_name = get_model_fullname(self)  
    if model_full_name in settings.NAVIGATED_MODELS:  
        queryset_name = '%s_query_set' % model_full_name  
        filtered_queryset_name = 'filtered_%s_query_set' % model_full_name  
        request.session[filtered_queryset_name] = self.get_preserved_filters(request) != ''  
        if hasattr(response, 'context_data') and 'cl' in response.context_data:  
            request.session[queryset_name] = list(response.context_data["cl"].queryset.values('pk'))  
    return response
```



submit a form in a web application -> the browser sends a POST request to the server with the form data.
In the case of the Django admin, when you submit a search form on a changelist view, the form data typically includes the search term entered by the user.  In Django admin, if the server determines that the search form was submitted successfully, it will typically redirect the user back to the same URL using a 302 status code. This is known as a "POST-redirect-GET" pattern.



