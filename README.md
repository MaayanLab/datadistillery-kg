# Data Distillery Knowloedge Graph
This documents how to process data provided by UBKG to the format used by the UI.

## Install Requirements
```
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
``` 

## Serialization
`src/Serialization.ipynb` reads the following files from the UBKG:
* `CODEs.csv` and `CUI-CODEs.csv` for the mapped ids
* `CUI-SUIs.csv` for the labels
* `CUI-CUIs.csv` for all edges

### Getting DCC/SAB specific nodes and edges

The code can take a specific SAB and returns a dataframe containing all edges under that SAB:

```
sab = 'LINCS'
dcc = 'LINCS'
df = get_sab_df(sab, dcc)
```

To resolve the nodes, we define a dictionary that labels what the source and target nodes are based on the relationships:

```
relations = {
	"negatively_regulates": {
		"target": "Gene",
		"source": "Compound",
	},
	"positively_regulates": {
		"target": "Gene",
		"source": "Compound",
	},
	"in_similarity_relationship_with": {
		"source": "Compound",
		"target": "Compound",
	}
}

nodes = get_nodes(df, sab, relations)
```

## Running neo4j

This code utilizes docker to run neo4j v5:

```
docker-compose up neo4j-v5
```

Alternatively, if you have your neo4j on your kubernetes cluster, you can run the following command to access porsts 7474 and 7687

```
kubectl port-forward -n distillery deploy/neo4j-v5 7474
kubectl port-forward -n distillery deploy/neo4j-v5 7687
```

## Ingestion
`src/ingestion_notebook` ingests everything in the `out/sab/` folder. It utilizes unique constraints on the ID to ensure quick ingestion

## Creating the schema

`src/UI_Schema`  creates a schema for the user interface by parsing serialized data from `out/sab`. This schema should then be put inside public/schema of the knowledge graph UI code.