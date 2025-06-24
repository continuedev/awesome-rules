---
name: LanceDB Best Practices
---
## Do this

- Define your table schema using PyArrow or Pydantic models (not plain dicts).
- Validate data types and vector shapes before inserting.
- Use batch inserts for efficiency.
- Use filters in queries to narrow results.

## Example: Schema Definition

### Good (PyArrow)
```python
import lancedb
import pyarrow as pa

db = lancedb.connect("/tmp/lancedb")
schema = pa.schema([
    ("id", pa.int64()),
    ("name", pa.string()),
    ("embedding", pa.list_(pa.float32(), 128))
])
table = db.create_table("my_table", schema=schema)
```

### Good (Pydantic)
```python
from pydantic import BaseModel, Field
from typing import List
import lancedb

class Item(BaseModel):
    id: int
    name: str
    embedding: List[float] = Field(..., min_items=128, max_items=128)

db = lancedb.connect("/tmp/lancedb")
table = db.create_table("my_table", schema=Item)
```

### Bad (dict)
```python
# This will NOT work in LanceDB
schema = {
    "id": "int",
    "name": "str",
    "embedding": "vector[float32, 128]"
}
table = db.create_table("my_table", schema=schema)  # ❌
```

### Example: Data Validation and Insert

```python
import numpy as np
row = {
    "id": 1,
    "name": "example",
    "embedding": np.random.rand(128).astype(np.float32).tolist()
}
table.insert([row])
```

### Example: Querying

```python
results = table.search(np.random.rand(128).astype(np.float32)).where("name = 'example'").limit(5).to_pandas()
```

## Don't do this

- Don't use plain dicts for schema definition.
- Don't mix vector dimensions in the same table.
- Don't insert data without validation.
- Don't store sensitive paths or credentials in code. 