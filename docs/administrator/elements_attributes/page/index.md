# Page

## Specs

| |Value|Details|
|---|---|---|
| **Name** | Page |  |
| **Classification** | element ||
| **Parent** | [Session](../session/index.md) ||
| **Required** | yes ||
| **Syntax** | <Page\>||

See also: [ID](ID.md), [Descriptor](descriptor.md), [PageGroup](pagegroup.md)

## Description
The Page element is a child of the Session element. There can be multiple pages in a quiz session.
Among the many attributes allowed for this element, ID and Descriptor are the ones used to identify the Page.
The ID attribute is required but the Descriptor is not. However, during quiz validation, the combination of ID_Descriptor
must be unique throughout all the Page elements.

In some observer studies, each Page may represent a different patient.
It could also represent a time point of a Patient's clinical journey (planning, 3 month follow up, 6 month follow up etc.).
Another example could be that there are multiple pages for one patient, each page holding images that represent different cancer sites (e.g. primary and secondary tumours).


```
<Session>
  <Page ID="Patient 1" Descriptor="CT">
    ...
  </Page>
  <Page ID="Patient 2" Descriptor="CT">
    ...
  </Page>

</Session>
```
