## Database relationships

- one-to-one **(1-1)**
- one-to-many **(1-N)**
- many-to-many **(N-N)**

####Modified notations:
- Crow Foot Notation
	- one-to-zillions

![Example](https://i.gyazo.com/32d2582a074a766ac4d5987bda4e90cb.png)

- Numeral Notation
	- minimum
	- most likely
	- maximum
	- format: **[min, likely, max]**

#### ![sky blue](https://placehold.it/15/10fabc/000000?text=+) one-to-one
1. Embed
	- fields at the same level of document
	- sub-documents
2. Reference
	- same identifier in both documents

![Sub-document example](https://i.gyazo.com/709e30ed9f6446e81f7940ca6e495a38.png)

#### Splitting extra data:
	- leads to more complexity
	- better performance
![](https://i.gyazo.com/9530fda3d445b27bb5b1bd7d5e2de38f.png)

#### ![sky blue](https://placehold.it/15/10fabc/000000?text=+) one-to-many

1. Embed
	- fields at the same level of document
	- sub-documents
2. Reference
	- same identifier in both documents



#### ![sky blue](https://placehold.it/15/10fabc/000000?text=+) many-to-many

many-to-many => 2 x one-to-many
![](https://i.gyazo.com/e08f6904ce256b5ff90b9ceecd170d91.png)

The middle table is called jump table which stores the indexes for relation between a and b

Sometimes duplication is a better solution then referencing. It avoids joining data(faster querying) but consumes more memory