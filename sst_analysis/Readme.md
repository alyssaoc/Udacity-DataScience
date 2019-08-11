# Sea Surface Temperature analysis near Chaleston, SC

One Paragraph of project description goes here

## Background

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

What things you need to install the software and how to install them

```
https://console.cloud.google.com/marketplace/details/noaa-public/icoads?filter=category:science-research&id=23fff065-a7df-4
```

### Data

The source data for this analysis can be found on the Google Cloud Platform, Biq Query (https://console.cloud.google.com/marketplace/details/noaa-public/icoads?filter=category:science-research&id=23fff065-a7df-4ab5-a771-a41504773070). 

I used the NOAA ICOADS data set from 1662-2017 to collect observed sea surface temperatures. All raw data files and the merged file are available in the /data folder. Observations without a sea surface temperature will not selected, as sea surface temperature is not easily inferred from other weather data. Observations were also parsed to a narrow geographic range between Savannah, GA and Myrtle Beach, SA for Lattitude 32-34 N and Longitude 79 to 81 W. Charleston, SC is located at 32.7765 N, 79.9311 W. 

```
#standardSQL
SELECT 
 timestamp, latitude, longitude, id_indicator, sst_measurement_method, sea_surface_temp
FROM
#  `bigquery-public-data.noaa_icoads.icoads_core_1662_2000`,
  `bigquery-public-data.noaa_icoads.icoads_core_2017`
  
WHERE
  latitude > 32
  AND latitude < 34
  AND longitude < -79
  AND longitude > -81
  AND sea_surface_temp IS NOT NULL;
  
  Data files were merged using cat *.csv command
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo

## Running the tests

Explain how to run the automated tests for this system

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc
