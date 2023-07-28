# CSS-AAS-OWL
A bidirectional mapping approach to transform capabilities and skills from AAS to OWL representation

## Overview
This repository contains mapping rules that can be used to convert a capability and skill model from an Asset Administration Shell (AAS) into an OWL ontology and vice versa. The approach is built on the current version of the AAS submodel specifications for "Capability" and "Control Component" as defined by the [IDTA](https://industrialdigitaltwin.org/en/content-hub/submodels) and our [capability and skill ontology for manufacturing](https://github.com/aljoshakoecher/caskman).
There is currently not a dedicated bidirectional mapping approach for AAS / JSON and ontologies. Thus, the following two unidirectional mapping approaches are combined to have mappings for both directions:
- [RDF Mapping Language (RML)](https://rml.io/) is used to map an AAS in JSON serialization into an ontology. All RML mapping rules are provided in the directory `rml`.
- [RDF Mappings to Exchange Formats (RDFex)](https://github.com/hsu-aut/rdfex) are used for the inverse direction, i.e., to map from an ontology to an AAS in JSON serialization. Please note, that the ontology must adher to [our ontology](https://github.com/aljoshakoecher/caskman). All RDFex mapping rules are provided in the directory `rdfex`.

Please note that all 

## How to use
First clone or download this repository in order to have all mapping rules on your local machine. Then, in order to execute mappings, you have to download the mapping execution engines provided by RML and RDFex. Both RML and RDFex provide CLI applications that can be used to execute the respective mappings.
The releases of RML are available [here](https://github.com/RMLio/rmlmapper-java/releases). Simply download the .jar from the assets section of the latest release.
The releases of RDFex can be found [here](https://github.com/hsu-aut/rdfex/releases). Simply download the CLI .jar from the assets section of the latest release.

In order to execute an RML mapping, execute the following command:<br>
`java -jar rml-mapper.jar -m <rml-mapping you want to execute> -o <your output file>`<br>
Make sure to provide a proper path to your RML mapper CLI (might depend on the version you have) and specify the paths for the mapping to be executed as well as your output file (optional). There are additional options (e.g., ontology serialization), please have a look at the [RML CLI documentation](https://github.com/RMLio/rmlmapper-java#cli).

In order to execute an RDFex mapping, execute the following command:<br>
`java -jar rdfex-mapper.jar -m <rdfex-mapping you want to execute> -o <your output file>`<br>
Make sure to provide a proper path to your RDFex mapper CLI (might depend on the version you have) and specify the paths for the mapping to be executed as well as your output file. For additional information, please have a look at the [RDFex documentation](https://github.com/hsu-aut/rdfex#rdfex---a-generic-mapping-language-to-transform-rdf-graphs-into-data-exchange-formats).

## Questions and Problems
If you have any questions, suggestions for improvements or in case you encounter bugs, please don't hesitate to open a [new issue](https://github.com/hsu-aut/CSS-AAS-OWL/issues/new/choose).

## How to cite
We encourage reuse and extensions of this project but would like to get mentioned in case you built on this mapping approach. This implementation is part of a research paper. If you want to use the mapping in your research work, please cite this paper with this BibTex information:
```
@misc{dKG+_TowardaMappingof_03.07.2023,
   author = {{da Silva}, Luis Miguel Vieira and K{\"o}cher, Aljosha and Gill, Milapji Singh and Weiss, Marco and Fay, Alexander},
   year = {03.07.2023},
   title = {{Toward a Mapping of Capability and Skill Models using Asset Administration Shells and Ontologies}},
   url = {https://arxiv.org/pdf/2307.00827},
   abstract = {In order to react efficiently to changes in production, resources and their functions must be integrated into plants in accordance with the plug and produce principle. In this context, research on so-called capabilities and skills has shown promise. However, there are currently two incompatible approaches to modeling capabilities and skills. On the one hand, formal descriptions using ontologies have been developed. On the other hand, there are efforts to standardize submodels of the Asset Administration Shell (AAS) for this purpose. In this paper, we present ongoing research to connect these two incompatible modeling approaches. Both models are analyzed to identify comparable as well as dissimilar model elements. Subsequently, we present a concept for a bidirectional mapping between AAS submodels and a capability and skill ontology. For this purpose, two unidirectional, declarative mappings are applied that implement transformations from one modeling approach to the other - and vice versa.},
}
```
Furthermore, we would like to hear from you in case you make use of this repo. Please don't hesitate to contact us.

## Roadmap
There are some possible extensions which are on our roadmap:
- Bundle both RML and RDFex CLI into one application to ease mapping execution
- Provide a webservice to execute mappings in a more convenient way
