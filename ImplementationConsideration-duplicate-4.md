<p id="breadcrumb">

[Implementation Guidance](https://simplifier.net/guide/OntarioLaboratoriesInformationSystemConsumerQuery/ImplementationGuidance) > Implementation Consideration

</p>


# Conformance Rules

The contents of a resource and the formats used to represent resources SHALL conform to the rules described in FHIR specification, as defined in the narrative of the specification, and as controlled by the conformance properties defined at: 

https://www.hl7.org/fhir/STU3/conformance-rules.html 

Data elements defined in resources and data types have three properties that are directly related to conformance: Cardinality, Is-Modifier, and Must-Support. These interact to place conformance requirements on implementations. 


# Implementation Consideration
Within OLIS, there is a broad range of concepts including patients, providers, organizations, systems, diagnostic procedures, test requests and results that require accurate identification.

Identifiers relevant to this interface include:

•	**Organization Identifiers** and **Service Provider Identifiers** 

•	**Patient Identifier**  is used to identify the person and is issued by Service Ontario and referred to as the Ontario Health Card

•	**Terminology:** the various coded values which are used to describe clinical concepts within health records as well as codes used within messages to meet the structural requirements of interfaces.

- Test Request Nomenclature Valid Test Request code(s) in the most recent OLIS Nomenclature file published

- Test Result Nomenclature: Valid Test Result code(s) in the most recent OLIS Nomenclature file published

- Specimen Source: Specimen Source code(s) in the most recent OLIS Nomenclature file published

(Refer to the latest OLIS Nomenclature file)

## MustSuport Flag

To maximize interoperability, this implementation guide uses MustSupport flag to identify elements that implementers must understand in order to properly submit data in the request and interpret the data in the response. Please refer to the guidance below:

* Elements marked with "MustSupport" flag in FHIR request must be provided by sending systems in accordance with the profile definition and associated business rules. If the FHIR request does not contain sufficient data, OLIS will return an error.

* Elements without "MustSupport" flag in FHIR request will be ignored by OLIS and no error will be generated because these elements are present.

* Elements marked with "MustSupport" in FHIR response will be supported in accordance with the definition in the profile. If the element is present, the consuming application SHALL handle the element in a meaningful way.(e.g. store it, use it in subsequent workflow or business function)

* Elements without "MustSupport" flag in FHIR response will not be populated by OLIS, therefore the consuming application can safely ignore them.

## Letter Case

Information in Ontario’s EHR assets is stored as mixed case and information is preserved in the format provided by the source (e.g. ALL UPPER CASE, Mixed Case, or a mix).  EHR consumers MAY apply data formatting rules where there is a local requirement to standardize information to a consistent format.

## French Characters

Information within Ontario’s EHR assets includes UTF-8 encoded French characters as provided by the source.

## Content Types and Encoding

The formal MIME-type for FHIR® resources is application/fhir+json or application/fhir+xml. The correct mime type SHALL be used by clients and servers:

* JSON (preferred): application/fhir+json

* XML (optional): application/fhir+xml

FHIR® uses UTF-8 for all request and response bodies. Since the HTTP specification defines a default character encoding of ISO-8859-1, requests and responses SHALL explicitly set the character encoding to UTF-8 using the charset parameter of the MIME-type in the Content-Type header. Requests MAY also specify this charset parameter in the Accept header and/or use the Accept-Charset header.



## Complex extension

Extensions can also contain extensions, either because the extension definition itself defines complex content - that is, a nested tree of values in the extension - or because the extension is extended with an additional extension defined separately.
In the case where an extension defines complex content, the identity of the parts of the extension is local/relative to the reference to the extension definition.
As an example, consider extending a patient with an opt-in status for a clinical trial containing 3 fields: clinical trial number, period of involvement, and a reason for enrollment.


XML

~~~~
<Patient>
  <extension url="http://hl7.org/fhir/StructureDefinition/patient-clinicalTrial" >
    <extension url="NCT" >
      <valueString value="123456789" />
    </extension>
    <extension url="period" >
      <valuePeriod>
        <start value="2009-03-14" />
      </valuePeriod>
    </extension>
    <extension url="reason" >
      <valueCodeableConcept>
        <coding>
          <system value="http://acme.org/codes/general" />
          <code value="tt14j" />
        </coding>
      </valueCodeableConcept>
    </extension>
  </extension>
  <!-- other data for patient -->
</Patient>
~~~~

JSON

~~~~
{
  "resourceType" : "Patient",
  "extension" : [{
    "url" : "http://hl7.org/fhir/StructureDefinition/patient-clinicalTrial",
    "extension" : [{
      "url" : "NCT",
      "valueString" : "123456789"
    }, {
      "url" : "period",
      "valuePeriod" : {
         "start" : "2009-03-14"
      }
      },  {
      "url" : "reason",
      "valueCodeableConcept" : {
          "coding" : [{
             "system" : "http://acme.org/codes/general",
             "code" : "tt14j"
          }]
       }
    }]
  }]
}

~~~~

As the URL suggests, this extension is defined as part of this specification.
This extension can be extended again, by adding a “registrar” extension:
The registrar is defined as a separate extension (e.g. by an implementing organization) rather than part of the official clinical-trial extension. The URL of the extension is thus different.


XML:

~~~~

<Patient>
  <extension url="http://hl7.org/fhir/StructureDefinition/patient-clinicalTrial" >
    <extension url="NCT" >
      <valueString value="123456789" />
    </extension>
    <extension url="period" >
      <valuePeriod>
        <start value="2009-03-14" />
        </valuePeriod>
    </extension>
    <extension url="reason" >
      <valueCodeableConcept>
        <coding>
          <system value="http://acme.org/codes/general" />
          <code value="tt14j" />
        </coding>
      </valueCodeableConcept>
    </extension>
  </extension>
    <extension url="http://acme.org/fhir/StructureDefinition/registrar" >
      <valueReference>
        <reference value="Practitioner/example" />
      </valueReference>
    </extension>
  <!-- other data for patient -->
</Patient>

~~~~

JSON:

~~~~

{
	"resourceType": "Patient",
	"extension": [{
		"url": "http://hl7.org/fhir/StructureDefinition/patient-clinicalTrial",
		"extension": [{
			"url": "NCT",
      	"valueString": "123456789"
		},
		{
			"url": "period",
			"valuePeriod": {
				"start": "2009-03-14"
			}
		},
		{
			"url": "reason",
			"valueCodeableConcept": {
				"coding": [{
					"system": "http://acme.org/codes/general",
					"code": "tt14j"
				}]
			}
		},
		{
			"url": "http://acme.org/fhir/StructureDefinition/registrar",
			"valueReference": {
				"reference": "Practitioner/example"
			}
		}]
	}]
}

~~~~


## Data Type Notes

### Date

A date, or partial date (e.g. just year or year + month) as used in human communication. There is no time zone. Dates SHALL be valid dates.

Regex: -?[0-9]{4}(-(0[1-9]|1[0-2])(-(0[0-9]|[1-2][0-9]|3[0-1]))?)?

Example:  1951-06-04


### DateTime



A date, date-time or partial date (e.g. just year or year + month) as used in human communication. If hours and minutes are specified, a time zone SHALL be populated. Seconds must be provided due to schema type constraints but may be zero-filled and may be ignored. Dates SHALL be valid dates. The time "24:00" is not allowed.

Regex: -?[0-9]{4}(-(0[1-9]|1[0-2])(-(0[0-9]|[1-2][0-9]|3[0-1])(T([01][0-9]|2[0-3]):[0-5][0-9]:[0-5][0-9](\.[0-9]+)?(Z|(\+|-)((0[0-9]|1[0-3]):[0-5][0-9]|14:00)))?)?)?


Example:  1951-06-04T10:57:34-05:00


## URI

A Uniform Resource Identifier Reference (RFC 3986). Note: URIs are case sensitive. For UUID (urn:uuid:53fefa32-fcbb-4ff8-8a92-55ee120877b7) use all lowercase.

URIs can be absolute or relative, and may have an optional fragment identifier.

## Supported Attributes

Only attributes described in the subsections below will be supported.


## Format

OLIS will support JSON and XML formats. JSON is the preferred format.


### Slicing


One common feature of constraining Structure Definitions is to take an element that may occur more than once (e.g. in a list), and split the list into a series of sublists, each with different restrictions on the elements in the sublist with associated additional meaning. In FHIR®, this operation is known as "Slicing" a list. It is common to "slice" a list into sub-lists each containing just one element, effectively putting constraints on each element in the list. This technique can also be used on elements that do not repeat, but that have a choice of data types.
A number in the brackets after the element name refers to its slicing number.


## Logical ID

Each resource has an id element which contains the "logical id" of the resource assigned by the server responsible for storing it. Resources always have a known logical id except for a few special cases (e.g. when a new resource is being sent to a server to assign a logical id in the create interaction). The logical id is unique within the space of all resources of the same type on the same server. Once assigned by the server, the id is never changed.

The location of a resource instance is an absolute URI constructed from the server base address at which the instance is found, the resource type and the Logical ID, such as http://test.fhir.org/rest/Patient/123 (where 123 is the Logical Id of a Patient resource). When the location is an HTTP address, this address can generally be used to retrieve or manipulate the resource. Note that implementations SHOULD NOT assume that the location of a resource is always resolvable to an accessible server - it may be temporarily unavailable, or not available by policy (e.g. firewalls) or in some cases, it might not actually exist (e.g. use of resource outside a RESTful environment). Resources reference each other by their location. These references are allowed to be absolute or relative (see Resource References for further discussion).

When a resource is copied from one server to another server, the copy might or might not keep the same logical id on the new server. This depends on replication and server policy. For further details, see Managing Resource Identity (including "Consistent Resource Identification").

Logical ids (and therefore locations) are case sensitive. Logical Ids are always opaque, and external systems need not and should not attempt to determine their internal structure. A logical id SHALL always be represented in the same way in resource references and URLs. Ids can be up to 64 characters long, and contain any combination of upper and lowercase ASCII letters, numerals, "-" and ".".

In some contexts, resources are not associated with location on a RESTful server, either because they are only created transiently for transfer between systems, or the systems are not using RESTful servers. In these cases, resources may be assigned some kind of location anyway, for purposes of consistency, or they might not have an assigned logical id, and they are identified based on other kinds of identifiers. See Resolving references in Bundles for one method of using resources not associated with RESTful servers.

## Managing Search Parameters

This interaction searches a set of resources based on some filter criteria. The interaction can be performed by several different HTTP commands.

~~~~
GET [base]/[type]{?[parameters]{&_format=[mime-type]}}

~~~~

This searches all resources of a particular type using the criteria represented in the parameters.
All these search interactions take a series of parameters that are a series of name=value pairs encoded in the URL (See W3C HTML forms).
If the search fails (cannot be executed, not that there is no matches), the return value is a status code 4xx or 5xx with an OperationOutcome. If the search succeeds, the return content is a Bundle with type = searchset containing the results of the search as a list of resources in a defined order.

## Search Parameter Types

| Type  |Description   |
|---|---|
|  number | Search parameter SHALL be a number (a whole number, or a decimal).  |
| date  | Search parameter is on a date/time. The date format is the standard XML format.  |
| string  | Search parameter is a simple string, like a name part. Search is case-insensitive and accent-insensitive. May match just the start of a string. String parameters may contain spaces.  |
| token  |  Search parameter on a coded element or identifier. May be used to search through the text, displayname, code and code/codesystem (for codes) and label, system and key (for identifier). Its value is either a string or a pair of namespace and value, separated by a pipe, depending on the modifier used. |

## Prefixes

For the ordered parameter types of number, date, and quantity, a prefix to the parameter value may be used to control the nature of the matching. To avoid URL escaping and visual confusion, the following prefixes are used:


| Prefix | Description | Details |
|----|---------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ge | the value for the parameter in the resource is greater or equal to the provided value | the range above the search value intersects (i.e. overlaps) with the range of the target value, or the range of the search value fully contains the range of the target value |
| le | the value for the parameter in the resource is less or equal to the provided value    | the range below the search value intersects (i.e. overlaps) with the range of the target value or the range of the search value fully contains the range of the target value  |

If no prefix is present, the prefix eq is assumed.

Note: Only 2 prefixes ‘ge’ and ‘le’ are supported for date related parameters.

*Numeric Examples*

| Example    | Description                                                      |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| [parameter]=100    | Values that equal 100, to 3 significant figures precision, so range [99.5 ... 100.5)                                                      |
| [parameter]=100.00 | Values that equal 100, to 5 significant figures precision, so range [99.995 ... 100.005). Whole numbers also equal 100.00, but not 100.01 |
| [parameter]=le100  | Values that are less or equal to 100                                                                                                      |
| [parameter]=ge100  | Values that are greater or equal to 100  

<br>

*Date Range Example*

To search for all the observations in a patient compartment that occurred over a 2 year period:


~~~~

GET [base]/Patient/23/Observation?date=ge2010-01-01&date=le2011-12-31
~~~~

*Quantity Examples*

A quantity parameter searches on the Quantity data type. The syntax for the value follows the form:
* [parameter]=[prefix][number]|[system]|[code] matches a quantity with the given unit
The prefix is optional, and is as described above, both regarding how precision and comparator/range operators are interpreted. 
<br>

*Example searches:*

Search for all the observations with a value of 5.4 mg where mg is understood as a UCUM unit (system/code)

~~~~

GET [base]/Observation?value=5.4|http://unitsofmeasure.org|mg

~~~~

Search for all the observations with a value of 5.4 mg where the unit - either the code or the stated human unit (unit) are "mg"

~~~~

GET [base]/Observation?value=5.4||mg

~~~~

Search for all the observations where the value of is less than 5.4 mg where mg is understood as a UCUM unit

~~~~

GET [base]/Observation?value=le5.4|http://unitsofmeasure.org|mg

~~~~


# Managing Returned Resources


## Paging

The server provides next set for the results of a search interaction for sending continuation links to the client when returning a Bundle.
This example shows the next page of a search result:

~~~~

<Bundle xmlns="http://hl7.org/fhir">
  <!-- snip metadata -->
  <!-- This Search. url starts with base search, and adds the effective
    parameters, and additional parameters for search state. All searches
    SHALL return this value.

	  In this case, the search continuation method is that the server
    maintains a state, with page references into the stateful list.
	-->
  <link>
    <relation value="self">


    <url value="[base]/DiagnosticReport?patient.identifier=[id-system-global-base]/ca-on-patient-hcn|1008624486&patient.gender=male&patient.birthdate=1929-11-29&issued=ge2016-01-02&_count=10&search-id=017-11-16T20:37:03.0000000X128987"/>
  </link>

  <link>
    <relation value="next"/>
    <url value="[base]/DiagnosticReport?patient.identifier=[id-system-global-base]/ca-on-patient-hcn|1008624486&patient.gender=male&patient.birthdate=1929-11-29&issued=ge2016-01-02&_count=10&search-id=017-11-16T20:37:03.0000000X128987"/>
  </link>

  <!-- then the search results... -->
</Bundle>

~~~~

A server will inform the client of the total number of resources returned by the interaction for which the results are paged using the Bundle.total.

## Page Count

In order to keep the load on clients, server and the network minimized, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. Page links are contained in the returned bundle as links.
Server will provide its own parameters in the links that it uses to manage the state of the search as pages are retrieved. These parameters do not need to be understood or processed by the client.
The parameter _count is defined as a hint to the server regarding how many resources should be returned in a single page. Server will not return more resources than requested, but is allowed to return less than the client requested. The server might define a configurable default and maximal values for count. The server will repeat the original _count parameter in its returned page links so that subsequent paging requests honor the original _count.

## Server Conformance

In order to allow the client to be confident about what search parameters were used as criteria by the server, the server will return the parameters that were actually used to process the search. Applications processing search results SHALL check these returned values where necessary. For example, if the server did not support some of the filters specified in the search, a client might manually apply those filters to the retrieved result set, display a warning message to the user or take some other action.
In the case of a RESTful search, these parameters are encoded in the self link in the bundle that is returned:
~~~~

<link>
    <relation value="self"/>
    <url value="[base]/DiagnosticReport?patient.identifier=[id-system-global-base]/ca-on-patient-hcn|12345678"/>
  </link>

~~~~

In other respects, servers have considerable discretion with regards to supporting search:
* Server will declare additional parameter search-id in the profiles referenced from their conformance statements. This search-id will be used for continuation pointer.
* Parameter names and URLs are case-sensitive.
* Server will return up to 25 results per page.




