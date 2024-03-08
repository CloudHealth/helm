# Changelog

All notable changes for each upgraded tag of the CloudHealth Container Collector image.  Found on DockerHub: https://hub.docker.com/r/cloudhealth/container-collector

The agent has been verified against:

[Kubernetes Versions ≥ 1.12](https://kubernetes.io/releases/)</br>
[Kubernetes Versions ≤ 1.26](https://kubernetes.io/releases/)</br>
[OC Version ≥ 4.1](https://docs.openshift.com/container-platform)

All versions before June 20, 2022 have been deprecated.

## [1458] - 2024-03-11

### Added

* PersistentVolumes, PersistentVolumeClaims, Ingress and Service collected to prepare for comprehensive Kubernetes Cost Calculation

### Security

* Vulnerabilities patched:
  * https://avd.aquasec.com/nvd/cve-2024-22365
  * https://avd.aquasec.com/nvd/cve-2023-52425
  * https://avd.aquasec.com/nvd/cve-2023-52426
  * https://avd.aquasec.com/nvd/cve-2023-52425
  * https://avd.aquasec.com/nvd/cve-2023-52426
  * https://avd.aquasec.com/nvd/cve-2023-6780
  * https://avd.aquasec.com/nvd/cve-2023-6246
  * https://avd.aquasec.com/nvd/cve-2023-6779
  * https://avd.aquasec.com/nvd/cve-2023-6780
  * https://avd.aquasec.com/nvd/cve-2023-6246
  * https://avd.aquasec.com/nvd/cve-2023-6779
  * https://avd.aquasec.com/nvd/cve-2023-6780
  * https://avd.aquasec.com/nvd/cve-2023-6246
  * https://avd.aquasec.com/nvd/cve-2023-6779
  * https://avd.aquasec.com/nvd/cve-2023-5981
  * https://avd.aquasec.com/nvd/cve-2024-0553
  * https://avd.aquasec.com/nvd/cve-2024-0567
  * https://avd.aquasec.com/nvd/cve-2023-48795
  * https://avd.aquasec.com/nvd/cve-2023-0767
  * https://avd.aquasec.com/nvd/cve-2024-0727
  * https://avd.aquasec.com/nvd/cve-2024-0727
  * https://avd.aquasec.com/nvd/cve-2023-4641
  * https://avd.aquasec.com/nvd/cve-2023-29383
  * https://avd.aquasec.com/nvd/cve-2023-4641
  * https://avd.aquasec.com/nvd/cve-2023-29383
  * https://avd.aquasec.com/nvd/cve-2023-4641
  * https://avd.aquasec.com/nvd/cve-2023-29383
  * https://avd.aquasec.com/nvd/cve-2023-7104
  * https://avd.aquasec.com/nvd/cve-2023-33202
  * https://avd.aquasec.com/nvd/cve-2023-33202
  * https://avd.aquasec.com/nvd/cve-2023-33201
  * https://avd.aquasec.com/nvd/cve-2023-33201
  * https://avd.aquasec.com/nvd/cve-2023-33202
  * https://avd.aquasec.com/nvd/cve-2023-33202

## [1423] - 2023-12-14

### Added

* The collector docker image now supports the "endpoint prefix" environment variable as a replacement for the "region"
environment variable. This variable should be set to the endpoint prefix provided by CloudHealth.


## [1405] - 2023-11-06

### Added

* The collector docker image now contains more debugging logs for setting the new "region" environment variable.

## [1398] - 2023-10-18

### Added

* The collector docker image now supports the "region" environment variable. This variable should be set to the region provided by CloudHealth corresponding to the CloudHealth region where your VMware Tanzu CloudHealth account is onboarded.

## [1360] - 2023-07-19

### Added

* The collector docker image now supports collecting the UID and kubernetes agent version.

## [1325] - 2023-05-18

### Changed

* Updated base image for the CloudHealth Container Collector image to [Photon v.5](https://hub.docker.com/_/photon)

## [1308] - 2023-02-22

### Security

* Assigned ID to the container's user within the Dockerfile to allow for use of `runAsNonRoot` security context option.

## [1307] - 2023-02-16

### Security

* Vulnerabilities patched:
  * [CVE-2023-0286](https://nvd.nist.gov/vuln/detail/CVE-2023-0286)
  * [CVE-2022-25857](https://nvd.nist.gov/vuln/detail/CVE-2022-25857)
  * [CVE-2022-3996](https://nvd.nist.gov/vuln/detail/CVE-2022-3996)
  * [CVE-2022-42003](https://nvd.nist.gov/vuln/detail/CVE-2022-42003)
  * [CVE-2022-42004](https://nvd.nist.gov/vuln/detail/CVE-2022-42004)
  * [CVE-2022-43551](https://nvd.nist.gov/vuln/detail/CVE-2022-43551)


## [1285] - 2022-12-01

* Base Alpine image updated to 
[tag 3.17.0](https://hub.docker.com/layers/library/alpine/3.17.0/images/sha256-c0d488a800e4127c334ad20d61d7bc21b4097540327217dfab52262adc02380c?context=explore), 
patching multiple vulnerabilities

## [1263] - 2022-11-14

### Fixed

* Resolves intermittent java.security.InvalidAlgorithmParameterException in arm64-compatible image. 

## [1225] - 2022-10-06

### Added

* Multi-platform support for the collector image.  The Docker image now supports both arm64 & amd64 architecture.

## [1222] - 2022-09-21

### Added

* Curl command added for troubleshooting assistance

## [1203] - 2022-08-10

### Added

* Liveness Check for collector pod
  * Added a new file liveness.txt in collector pod /tmp folder. Every time collection is performed for any resource, the
    file's access date timestamp is updated.

## [1201] - 2022-08-09

### Removed

* Removed triggering requests to errors endpoint

## [1191] - 2022-07-25

### Added

* Functionality to collect additional resources from the Kubernetes API including:
  * ResourceQuotas
  * LimitRanges
  * Deployments
  * ReplicaSets
  * StatefulSets
  * DaemonSets
  * CronJobs

* Functionality to collect pod metrics from Kubernetes metrics-server
* Error handling added to provide better debug logging while retrieving data from Kubernetes API

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
