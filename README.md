# PagerDuty Client

PagerDuty Client aims to provide a full flexed Java client which is easy to use and integrates seamlessly
with PagerDuty REST API.

## Getting started

PagerDutyClient requires an ApiAccessKey in order to be created. This ApiAccessKey (Api Token) will be used for
authentication purposes when calling PagerDuty REST API. For more information about PagerDuty API Token Authentication
refer to [PagerDuty API Token Authentication](https://v2.developer.pagerduty.com/docs/authentication)

```
PagerDutyClient pagerDutyClient = PagerDutyClient.create("YOUR_API_ACCESS_KEY");
```

The library supports the creation of three different type of incidents. For your reference, below are examples
on how to create each incident type as well as how to use PagerDutyClient to perform the according operation:

- trigger: This will send a new 'trigger' incident to PagerDuty containing the details specified in the IncidentBuilder.
A helper IncidentBuilder is provided for the sake of simplicity to ease with the creation of trigger incidents. The
trigger event requires two mandatory parameters:
  - service_key (The GUID of one of your "Generic API" services. This is the "Integration Key" listed on a Generic
    API's service detail page.)
  - description: Text that will appear in the incident's log associated with this event.
More details can be provided to the incident as previously mentioned by calling the available methods offered by the
IncidentBuilder.
```
Incident incident = Incident.IncidentBuilder
        .trigger("SERVICE_KEY", "INCIDENT DESCRIPTION")
        .client("Creacodetive - PagerDutyClient")
        .clientUrl("http://www.creacodetive.com")
        .details("This is an incident test to test PagerDutyClient")
        .build();
pagerDutyClient.trigger(incident);
```

- acknowledge: This will send a new acknowledge incident to PagerDuty based upon the 'serviceKey' and 'incidentKey'
provided.
```
Incident incident = Incident.IncidentBuilder.acknowledge("SERVICE_KEY", "INCIDENT_KEY");
pagerDutyClient.acknowledge(incident);
```

- resolve: This will send a new resolve incident to PagerDuty based upon the 'service_key' and 'incident_key' provided.
```
Incident incident = Incident.IncidentBuilder.resolve("SERVICE_KEY", "INCIDENT_KEY");
pagerDutyClient.resolve(incident);
```

## Lib integration:

The library uses SL4J facade for logging purposes. Thus, making it fully flexible for integration with other
projects whereby a specific logging implementation is already being used (e,g: log4j, logback, etc).

## Contributing

- Fork it!
- Create your feature branch: git checkout -b my-new-feature
- Commit your changes: git commit -am 'Add some feature'
- Push to the branch: git push origin my-new-feature
- Submit a pull request :D

## Authors

Daniel I. Khan Ramiro - Cisco Systems
See also the list of [contributors](https://github.com/dikhan/pagerduty-client/graphs/contributors) who participated in this project.

## Acknowledgements:

ApiService calls: http://unirest.io/java.html
Java objects serialization: https://github.com/FasterXML/jackson
Testing: http://www.mock-server.com/

## License

TBD