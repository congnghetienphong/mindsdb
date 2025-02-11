# Deleting a Predictor

## Using the `db.predictors.deleteOne()` Method

### Description

The `db.predictors.deleteOne()` method deletes an ML model specified in its argument.

### Syntax

```sql
db.predictors.deleteOne({name: "predictor_name"});
```

On execution, we get:

```json
{
    "acknowledged" : true,
    "deletedCount" : 1
}
```

Where:

| Name               | Description                     |
| ------------------ | ------------------------------- |
| `name`             | Name of the model to be deleted |

## Example

### Listing All the Predictors

Before deleting a predictor, let's list all the available predictors using the `db.predictors.find()` method.

```sql
db.predictors.find({});
```

On execution, we get:

```json
{
    "name": "home_rentals_model",
    "status": "complete",
    "accuracy": "1.0",
    "predict": "rental_price",
    "update_status": "up_to_date",
    "mindsdb_version": "22.8.3.1",
    "error": null,
    "select_data_query": "",
    "training_options": ""
},
{
    "name": "other_model",
    "status": "complete",
    "accuracy": "1.0",
    "predict": "rental_price",
    "update_status": "up_to_date",
    "mindsdb_version": "22.8.3.1",
    "error": null,
    "select_data_query": "",
    "training_options": ""
}
```

### Dropping a Predictor

The `db.predictors.deleteOne()` method drops the model collection called `home_rentals_model`.

```sql
db.predictors.deleteOne({name: "home_rentals_model"});
```

On execution, we get:

```json
{
    "acknowledged" : true,
    "deletedCount" : 1
}
```

### Validating the Deletion

You can validate that the model was removed by listing all the predictors.

```sql
db.predictors.find({});
```

On execution, we get:

```json
{
    "name": "other_model",
    "status": "complete",
    "accuracy": "1.0",
    "predict": "rental_price",
    "update_status": "up_to_date",
    "mindsdb_version": "22.8.3.1",
    "error": null,
    "select_data_query": "",
    "training_options": ""
}
```
