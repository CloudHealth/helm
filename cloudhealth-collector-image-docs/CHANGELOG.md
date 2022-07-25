# Changelog

All notable changes for each upgraded tag of the CloudHealth Container Collector image.  Found on DockerHub: https://hub.docker.com/r/cloudhealth/container-collector

The agent has been verified against:

[Kubernetes Versions ≥ 1.12](https://kubernetes.io/releases/)</br>
[Kubernetes Versions ≤ 1.23](https://kubernetes.io/releases/)</br>
[OC Version ≥ 4.1](https://docs.openshift.com/container-platform)

## [1191] - 2022-07-25
### Added
* Error handling added to provide better debug logging while retrieving data from Kubernetes API
* Separate metrics cache initialized in preparation for collecting usage data in the future

## [1183] - 2022-07-12
### Security
* JRuby removed from final image
* Unused jar libraries removed

## [1180] - 2022-06-17
### Security
* Upgraded to Alpine 3.16.0
* Ruby Libraries Upgraded as well as a few deprecated

## [1178] - 2022-06-15
### Added
* Functionality added to refresh the service account token periodically to prevent the use of expired tokens. 

## [1173] - 2022-05-19
### Security
* Libraries Upgraded
* Vulnerabilities patched: CVE-2020-10663, CVE-2020-28052, CVE-2020-36518, CVE-2021-37714, CVE-2020-15522, CVE-2015-6748

## [1172] - 2022-05-11
### Security
* Upgraded to Alpine 3.15.4

## [1155] - 2022-03-28
### Removed
* Removed jbundler

## [1119] - 2022-03-16
### Added
* Changelog introduced


