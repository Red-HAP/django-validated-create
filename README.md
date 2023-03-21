# django-validated-create

This is a cheap n' cheerful little module that will validate a Django model record's immediate foreign-key relations.

## validated_create

This function takes three arguments:

1. `model` (`django.db.models.Model`) : The destination model/table
2. `record` (`dict`) : The input record (dict keys match model field names)
3. `fetch_related` (`bool`) : Flag to fetch the full related record(s). Default is `False`

This will add any model defaults to a copy of `record` and set or change any other key values in order to build the insert and select statement. A single statement will be built that will build the insert and subsequent select of primary keys from the related data (if any). Finally, any foreign key specified in the output will be checked against the input. If the values are different, an `IntegrityError` exception will be raised.

If `fetch_related` is set to `True`, then the full related record will also be returned.

On success, the function will return a model instance created from the fetched data.

## validated_select

This function takes three arguments:

1. `model` (`django.db.models.Model`) : The destination model/table
2. `record` (`dict`) : The input record (dict keys match model field names)
3. `fetch_related` (`bool`) : Flag to fetch the full related record(s). Default is `False`

This will a select of model record as well as any primary keys from the related data (if any). Finally, any foreign key specified in the output will be checked against the input. If the values are different, an `IntegrityError` exception will be raised.

If `fetch_related` is set to `True`, then the full related record will also be returned.

On success, the function will return a model instance created from the fetched data.
