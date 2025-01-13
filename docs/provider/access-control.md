# Access Control

Access to data sources is controlled by roles and licences.

A [catalog entry](../metadata/) specifies one or more roles and a licence. If a participant has any of the roles, they may access the data source under the specified licence.

The Registry maintains a list of the permissions and obligations for access to a data source under a given licence.

Scheme-conforming data sources use [Scheme Catalog Requirements Documents](../../registry/scheme_catalog_requirements/) which specify the Access Rules for common formats of data sources.

## Changes from Open Energy

This access control specification is a simplification of Open Energy's access control. Open Energy was designed for one-to-many data products, which required the flexibility for each data provider to describe the individual access requirements for each of their products. Data sharing in a Trust Framework is many-to-many, where the access requirements are set by a sector-wide governance process.

This specification will be iterated as use cases emerge. The current expectation, reflected in this specification, is that the governance process will describe the minimum set of roles permitted to access data under a specific licence, and the data provider may be allowed to expand this to additional roles.

## Example

```
<https://data.example.com/supply-voltage/v0>
    a dcat:DataService ;
	# ...
    ib1:roleRequiredToAccess <https://registry.core.trust.ib1.org/scheme/electricity/role/report-provider> ;
    ib1:roleRequiredToAccess <https://registry.core.trust.ib1.org/scheme/electricity/role/archiver> ;
    dcterms:license <https://registry.core.trust.ib1.org/scheme/electricity/licence/voltage-reporting/1.4> ;
.
```

These rules specify that members of either the "Report Provider" and "Archivers" roles may access the data with the Scheme's Voltage Reporting licence.

