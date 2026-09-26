## Competency Questions

The Error Ontology can be used to produce an inconsistent model if a particular (and incorrect) situation happens.
In the following subsections, some competency questions are introduced together with their respective SPARQL queries.

The prefixes that are used in all the SPARQL queries provided below are defined as follows:

    PREFIX error: <http://www.essepuntato.it/2009/10/error#>
    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

### CQ1

Which resources are explicitly asserted to have an error, and what is the description of that error?

    SELECT ?resource ?description WHERE {
        ?resource error:hasError ?description .
    }

### CQ2

Which classes describe a forbidden situation, and what is the error description associated with their members?

    SELECT ?class ?description WHERE {
        ?class rdfs:subClassOf ?restriction .
        ?restriction a owl:Restriction ;
            owl:onProperty error:hasError ;
            owl:hasValue ?description .
    }

### CQ3

Does the dataset contain at least one resource with an error?

    ASK {
        ?resource error:hasError ?description .
    }