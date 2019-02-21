---
layout: default
title: CITE Participation Guide
collection: tools
permalink: /tools/citeguide/
---

# Community Interoperability Test Environment (CITE) Participation Guidance

Prepared By: The FPKI Technical Working Group (TWG)  <br>
An FPKI Policy Authority Working Group

Last Update: February 12th, 2019 <br>

## Overview

The Federal Public Key Infrastructure (FPKI) has been the subject of various transitions and evolutions during its years of existence. This includes hardware and software upgrades, configuration and architecture changes, implementation of higher complexity keys and algorithms, and implementation of new application capabilities. The impact on continued interoperability throughout these transitions has highlighted the need for an integrated test environment.

The Community Interoperability Test Environment (CITE) was established as the FPKI integrated test environment. CITE provides the FPKI community with a test environment that mimics the production FPKI hierarchy. It is operated by the Federal PKI Management Authority (FPKIMA) and contains a Test Federal Common Policy and Test Federal Bridge. The FPKIMA operated Test Common and Federal Bridge issue test CA certificates to participating Shared Service Providers, Federal Agency PKI, and Non-Federal Affiliates (referred to as FPKI Partners) to perform interoperability and other forms of testing outlined in this document. CITE has two main purposes:

1. Ensure proper functionality of system changes prior to production deployment, and
2. Identify and resolve technical issues across FPKI Partners.

The FPKI Community can use CITE to evaluate PKI or application changes in a test environment that mimics the production FPKI hierarchy and test potential interoperability issues before those changes are deployed to the FPKI. <br>

## Document Scope

This document provides guidelines and specifications for an FPKI Partner to participate in CITE. CITE Participants refer to an FPKI Partner establishing a test PKI certified or cross-certified with the Test Common Policy or Test Bridge CA. This document shall not define how CITE Participants conduct testing.

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119.

Modifications to this document and any waivers are controlled by the FPKI Technical Working Group. <br>

## Testing Use Cases

The main purpose of CITE is interoperability and infrastructure testing of PKI components and Relying Party applications. Additional types of testing may be identified and conducted as necessary and to the extent supported by CITE Participants. CITE should not be used for system stress testing. Infrastructure testing ensures that upgrades, patches, policy changes, new products, and any other changes to the production FPKI do not adversely affect interoperability.

Relying Party application testing ensures that application modules operate as intended. In addition, application testing ensures that the system performs as expected and can properly process transactions that rely on FPKI certificates.

Some examples of testing conducted in CITE include:
1. Interoperability testing between cross-certified Certification Authorities (CAs);
2. Transition testing to new algorithms (e.g., SHA-2, ECC);
3. PIV and PIV-I card interoperability testing;
4. Repository access testing when using content delivery networks, load balancers, or other networking configurations; and
5. Path discovery and/or validation testing for an application

When testing is successful in CITE, assurance is gained that the proposed change(s) will operate in the production FPKI as intended. When tests fail in the CITE, issues are identified and addressed without production FPKI impact. <br>

## Terms and Conditions

To ensure CITE provides effective services and comprehensive test results, each CITE participant should emulate its production environment as closely as possible in CITE. To the extent possible, the test environment should include the same products, logical architecture, and community integration relationships as in the production environment.

The closer the test environment is to the production, the more likely issues can be discovered and resolved early in the development and testing process. For example, if a Federal Agency PKI includes both HTTP and LDAP URIs in its production certificates, both types of URIs should be included in its CITE test certificates, along with operational repositories corresponding to those URIs. Therefore, both methods available in production can be tested in the CITE. <br>

## Technical Specifications

CITE participants shall follow the below technical specifications.

1. The CITE Participant services shall be internet accessible.
2. Repository availability and technical support should be maintained as detailed in the [Repository Availability](#repository-availability) and [Technical Support Availability](#technical-support-availability) sections.
3. Test environments should emulate the corresponding production environment as closely as possible
    1. Each CITE Participant CA hierarchy shall mimic their production environment. A CITE Participant may limit the number of included Test CAs to one certified or cross-certified CA and either an intermediate and/or issuing CA.
    2. All CAs shall be distinctly marked to denote it is a test CA. The word "Test" or "Development" should be used in the Distinguished Names (DNs).
    3. An exact production replica of all internal CA components (e.g. hardware security modules, network zones, or other non-internet accessible components) is not required.
    4. The CITE Participant repositories should match those in the corresponding production environment as accurately as possible, including operating system versions and patch levels, protocols, and product version and patch levels.
    5. All CITE Participant CA certificates, Certificate Revocation Lists (CRLs), and cross-certificates shall be publicly accessible in the associated repository.
    6. Certificate revocation information should, when applicable, be made available using the same mechanism(s) as in the production environment (e.g., OCSP, CRLs).
4. CITE Participants should provide expired, revoked, and valid test end-entity certificates, including private keys, for application and relying party tests. The sample certificates should be hosted on a publicly accessible directory or website and shared with the FPKI Technical Working Group. The website or directory address may be made available through this guide. CITE Participants should have test certificates representing each of the certificate policies and certificate types that are issued from the corresponding production environment.
5. All CITE Participant CAs and end-entity certificates should match their production counterparts, as applicable.
    1. Test certificates and CRL profiles (including version, key length, extensions, and syntax) shall match that of the production environment.
    2. The CITE CRLs may have a longer validation period than is required in production.
    3. The CITE CA certificates and cross-certificates shall depict the same trust relationships as in the production environment.
    4. CITE Participants should assert test certificate policy Object Identifiers (OIDs), when testing with CITE. See [Appendix A](#appendix-a) for test OIDs and their production equivalent.
    5. Resource references (such as CRL Distribution Points and Authority Information Access (AIA) points in the CITE certificates shall correspond to appropriately functional repositories.

{% include alert-warning.html content="If publicly posting private keys for testing purposes, the corresponding certificates are required to assert test certificate policy OIDs (see [Appendix A](#appendix-a) for test certificate policy OIDs)." %} <br>

## Scheduled and Unscheduled Testing

Testing and support requests (to include certificate issuance and management requests) shall be scheduled and coordinated in advance. This will allow CITE Participants to appropriately plan and schedule any technical support needed for successful testing.

{% include alert-info.html heading="Testing requests can be submitted to the FPKI Technical Working Group at fpki-ttips@listserv.gsa.gov. All testing requests should be submitted ten business days in advance." %} <br>

For unscheduled testing, the CITE and FPKI Partner repositories are internet accessible and available for testing (including vendors and other Relying Parties). Unscheduled testing may be conducted at any time if the below is true.
1. All parties involved agree to provide the necessary support; or
2. The testing party does not need support from any other CITE Participant (in which case, the testing party is willing to accept that services may or may not be available). <br>

## Repository Availability

CITE Participant repositories should be available during regular business hours for scheduled and unscheduled testing. Each CITE Participant should leave its repository services operational and available 24 hours a day, 7 days a week. CITE Participants should follow the below table on repository availability requirements.

| Days | Time | Description | Repository Availability Requirement |
| --------- | --------------- | ------------------ | ----------------------------------- |
| Mon - Fri | 0900 - 1700 EST | Business Hours     | CITE Participant repository services should be operational and available, except for scheduled downtime and federal holidays. |
| Mon - Fri | 1700 - 0900 EST | Non-Business hours | No requirement |
| Sat - Sun | 0001 - 0000 EST | Non-Business hours | No requirement |

{% include alert-warning.html content="CITE Test Common Policy and Test Federal Bridge, at a minimum, will provide 20% availability per month. CITE should not be used or relied upon for near-production availability." %} <br>

## Technical Support Availability

CITE Participants shall provide the FPKI Technical Working Group with email and phone information for at least two technical contactsto help coordinate any technical service issues. In lieu of providing individual names for technical POCs, CITE Participants may establish a group or other organizational-based email addresses for communications with the appropriate technical contacts. This information will only be made available (in a controlled manner) to CITE Participants, FPKI Applicants (if applicable), and vendors supporting the FPKI as needed during testing or troubleshooting. CITE Participants involved in scheduled testing shall provide the issuance, management, and troubleshooting necessary to help resolve any issues.

{% include alert-warning.html content="CITE Participant technical support is only available for scheduled testing with any outage resolved on a best effort basis. " %} <br>

## Test Websites

| FPKI Partner | Website URL |
| ------------ | ----------- |
| No test websites established at this time | |

## Appendix A 

### Policy Object Identifiers (OIDS) and Mapping Table

The table below lists the current test to production OID equivalent used by the FPKIMA and CITE Participants.

1. [Federal PKI Trust Infrascture Test OIDs](#federal-pki-trust-infrastructure-test-oids)
2. [Federal Agency PKI Test OIDs](#federal-agency-pki-test-oids)
3. [Federal Shared Service Provider (SSP) Test OIDs](#federal-shared-service-provider-ssp-test-oids)
4. [Non-Federal Issuer (NFI) Test OIDs](#non-federal-issuer-nfi-test-oids)
5. [Commercial PKI Bridge Test OIDs](#commercial-pki-bridge-test-oids)
6. [Deprecated Test OIDs](#deprecated-test-oids)

### Federal PKI Trust Infrastructure Test OIDs

#### Federal PKI Federal Bridge

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| 2.16.840.1.101.3.2.1.48.1 | FBCA Rudimentary       | 2.16.840.1.101.3.2.1.3.1 |
| 2.16.840.1.101.3.2.1.48.2 | FBCA Basic             | 2.16.840.1.101.3.2.1.3.2 |
| 2.16.840.1.101.3.2.1.48.3 | FBCA Medium            | 2.16.840.1.101.3.2.1.3.3 |
| 2.16.840.1.101.3.2.1.48.4 | FBCA Medium Hardware   | 2.16.840.1.101.3.2.1.3.12 |
| 2.16.840.1.101.3.2.1.48.5 | FBCA Medium CBP        | 2.16.840.1.101.3.2.1.3.14 |
| 2.16.840.1.101.3.2.1.48.6 | FBCA Medium Hardware CBP | 2.16.840.1.101.3.2.1.3.15 |
| 2.16.840.1.101.3.2.1.48.7 | FBCA High | 2.16.840.1.101.3.2.1.3.4 |
| 2.16.840.1.101.3.2.1.48.78 | id-fpki-certpcy-pivi-hardware | 2.16.840.1.101.3.2.1.3.18 |
| 2.16.840.1.101.3.2.1.48.79 | id-fpki-certpcy-pivi-cardAuth | 2.16.840.1.101.3.2.1.3.19 |
| 2.16.840.1.101.3.2.1.48.80 | id-fpki-certpcy-pivi-contentSigning | 2.16.840.1.101.3.2.1.3.20 |
| 2.16.840.1.101.3.2.1.48.99 | FBCA devices | 2.16.840.1.101.3.2.1.3.37 |
| 2.16.840.1.101.3.2.1.48.100 | FBCA devices Hardware | 2.16.840.1.101.3.2.1.3.38 |

#### Federal PKI Federal Common Policy

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| 2.16.840.1.101.3.2.1.48.8 | id-fpki-common-policy | 2.16.840.1.101.3.2.1.3.6 |
| 2.16.840.1.101.3.2.1.48.9 | id-fpki-common-hardware | 2.16.840.1.101.3.2.1.3.7 |
| 2.16.840.1.101.3.2.1.48.10 | id-fpki-common-devices | 2.16.840.1.101.3.2.1.3.8 |
| 2.16.840.1.101.3.2.1.48.11 | id-fpki-common-authentication | 2.16.840.1.101.3.2.1.3.13 |
| 2.16.840.1.101.3.2.1.48.12 | id-fpki-common-High | 2.16.840.1.101.3.2.1.3.16 |
| 2.16.840.1.101.3.2.1.48.13 | id-fpki-common-cardAuth | 2.16.840.1.101.3.2.1.3.17 |
| 2.16.840.1.101.3.2.1.48.86 | id- fpki-common-piv-contentSigning | 2.16.840.1.101.3.2.1.3.39 |
| 2.16.840.1.101.3.2.1.48.98 | id-fpki-common-devicesHardware | 2.16.840.1.101.3.2.1.3.36 |
| 2.16.840.1.101.3.2.1.48.109 | id-fpki-common-pivAuth-derived | 2.16.840.1.101.3.2.1.3.40 |
| 2.16.840.1.101.3.2.1.48.110 | id-fpki-common-pivAuth-derived-hardware | 2.16.840.1.101.3.2.1.3.41 |

### Federal Agency PKI Test OIDs

#### Department of Defense (DoD)

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| 2.16.840.1.101.3.2.1.48.68 | id-US-dod-basic | 2.16.840.1.101.2.1.11.2 |
| 2.16.840.1.101.3.2.1.48.69 | id-US-dod-medium-2048 | 2.16.840.1.101.2.1.11.18 |
| 2.16.840.1.101.3.2.1.48.70 | id-US-dod-mediumhardware-2048 | 2.16.840.1.101.2.1.11.19 |
| 2.16.840.1.101.3.2.1.48.71 | id-US-dod-FORTEZZA | 2.16.840.1.101.2.1.11.4 |
| 2.16.840.1.101.3.2.1.48.72 | id-US-dod-type1 | 2.16.840.1.101.2.1.11.6 |
| N/A | id-US-dod-mediumNPE-2048 | 2.16.840.1.101.2.1.11.17 |
| N/A | id-US-dod-mediumNPE-112 | 2.16.840.1.101.2.1.11.36 |
| N/A | id-US-dod-mediumNPE-128 | 2.16.840.1.101.2.1.11.37 |
| N/A | id-US-dod-mediumNPE-192 | 2.16.840.1.101.2.1.11.38 |
| N/A | id-US-dod-medium-112 | 2.16.840.1.101.2.1.11.39 |
| N/A | id-US-dod-medium-128 | 2.16.840.1.101.2.1.11.40 |
| N/A | id-US-dod-medium-192 | 2.16.840.1.101.2.1.11.41 |
| N/A | id-US-dod-mediumHardware-112 | 2.16.840.1.101.2.1.11.42 |
| N/A | id-US-dod-mediumHardware-128 | 2.16.840.1.101.2.1.11.43 |
| N/A | id-US-dod-mediumHardware-192 | 2.16.840.1.101.2.1.11.44 |

#### Department of Defense External CA (DoD ECA)

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| N/A | ECA medium | 2.16.840.1.101.3.2.1.12.1 |
| N/A | ECA Medium Hardware | 2.16.840.1.101.3.2.1.12.2 |
| N/A | ECA Medium Token | 2.16.840.1.101.3.2.1.12.3 |

#### Department of Homeland Security (DHS)

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| 2.16.840.1.101.3.2.1.15.31 | id-dhs-certpcy-rudimentary | 2.16.840.1.101.3.2.1.15.1 |
| 2.16.840.1.101.3.2.1.15.32 | id-dhs-certpcy-basic | 2.16.840.1.101.3.2.1.15.2 |
| 2.16.840.1.101.3.2.1.15.33 | id-dhs-certpcy-medium | 2.16.840.1.101.3.2.1.15.3 |
| 2.16.840.1.101.3.2.1.15.34 | id-dhs-certpcy-high | 2.16.840.1.101.3.2.1.15.4 |
| 2.16.840.1.101.3.2.1.15.35 | id-dhs-certpcy-mediumHardware | 2.16.840.1.101.3.2.1.15.5 |

#### Department of State (DOS)

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| 2.16.840.1.101.3.2.1.48.49 | state-basic | 2.16.840.1.101.3.2.1.6.1 |
| 2.16.840.1.101.3.2.1.48.50 | state-low | 2.16.840.1.101.3.2.1.6.2 |
| 2.16.840.1.101.3.2.1.48.51 | state-moderate | 2.16.840.1.101.3.2.1.6.3 |
| 2.16.840.1.101.3.2.1.48.52 | state-high | 2.16.840.1.101.3.2.1.6.4 |
| 2.16.840.1.101.3.2.1.48.53 | state-mrtd | 2.16.840.1.101.3.2.1.6.100 |
| 2.16.840.1.101.3.2.1.48.77 | State Medium Hardware | 2.16.840.1.101.3.2.1.6.12 |

#### Department of the Treausry

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| 2.16.840.1.101.3.2.1.48.54 | treasury-cp1 | 2.16.840.1.101.3.2.1.5.1 |
| 2.16.840.1.101.3.2.1.48.55 | treasury-level 1 | 2.16.840.1.101.3.2.1.5.2 |
| 2.16.840.1.101.3.2.1.48.56 | treasury-level 2 | 2.16.840.1.101.3.2.1.5.3 |
| 2.16.840.1.101.3.2.1.48.57 | treasury-level 3 | 2.16.840.1.101.3.2.1.5.4 |
| 2.16.840.1.101.3.2.1.48.58 | treasury-level 4 | 2.16.840.1.101.3.2.1.5.5 |
| 2.16.840.1.101.3.2.1.48.75 | Treasury Medium-Software | 2.16.840.1.101.3.2.1.5.7 |
| 2.16.840.1.101.3.2.1.48.76 | Treasury Basic Org | 2.16.840.1.101.3.2.1.5.8 |
| 2.16.840.1.101.3.2.1.48.111 | treasury-pivi-hardware | 2.16.840.1.101.3.2.1.5.10 |
| 2.16.840.1.101.3.2.1.48.112 | treasury-pivi-cardAuth | 2.16.840.1.101.3.2.1.5.11 |
| 2.16.840.1.101.3.2.1.48.113 | treasury-pivi-contentSigning | 2.16.840.1.101.3.2.1.5.12 |

#### GSA FIPS 201 Approved Product List (APL)

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| 2.16.840.1.101.3.2.1.48.248 | APL test lab Golden PIV-I Authentication | N/A |
| 2.16.840.1.101.3.2.1.48.249 | APL test lab Golden PIV-I CardAuth | N/A |
| 2.16.840.1.101.3.2.1.48.250 | APL test lab Golden PIV-I Key Management | N/A |
| 2.16.840.1.101.3.2.1.48.251 | APL test lab Golden PIV-I Digital Signature | N/A |
| 2.16.840.1.101.3.2.1.48.252 | APL test lab Golden PIV-I Content Signing | N/A |

#### Government Printing Office (GPO)

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| 2.16.840.1.101.3.2.1.48.37 | id-gpo-medium | 2.16.840.1.101.3.2.1.17.1 |

#### U.S. Patent and Trademark Office (USPTO)

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| 2.16.840.1.101.3.2.1.48.60 | pto-registered-practitioner | 2.16.840.1.101.3.2.1.2.1 |
| 2.16.840.1.101.3.2.1.48.61 | pto-inventor | 2.16.840.1.101.3.2.1.2.2 |
| 2.16.840.1.101.3.2.1.48.62 | pto-practitioner-employee | 2.16.840.1.101.3.2.1.2.3 |
| 2.16.840.1.101.3.2.1.48.63 | pto-basic | 2.16.840.1.101.3.2.1.2.4 |
| 2.16.840.1.101.3.2.1.48.64 | pto-service-provider | 2.16.840.1.101.3.2.1.2.5 |
| 2.16.840.1.101.3.2.1.48.65 | pto-service-provider-registrar | 2.16.840.1.101.3.2.1.2.6 |
| 2.16.840.1.101.3.2.1.48.66 | pto-basic-2003 | 2.16.840.1.101.3.2.1.2.7 |
| 2.16.840.1.101.3.2.1.48.67 | pto-medium-2003 | 2.16.840.1.101.3.2.1.2.8 |

#### National Aeronautics and Space Administration (NASA)

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| 2.16.840.1.101.3.2.1.48.74 | NASA | 1.3.6.1.4.1.71.1.1.103 |

### Federal Shared Service Provider (SSP) Test OIDs

See [Federal PKI Federal Common Policy](#federal-pki-federal-common-policy)

### Non-Federal Issuer (NFI) Test OIDs

#### Entrust Managed Services

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| 2.16.840.1.114027.200.3.10.10.1.8 | id-emspki-nfssp-rudimentary-policy | 2.16.840.1 .114027.200.3.10.7.8 |
| 2.16.840.1.114027.200.3.10.10.1.7 | id-emspki-nfssp-basic-policy | 2.16.840.1.114027.200.3.10.7.7 |
| 2.16.840.1.114027.200.3.10.10.1.3 | id-emspki-nfssp-medium-policy | 2.16.840.1.114027.200.3.10.7.1 |
| N/A | id-emspki-nfssp-medium-devices | 2.16.840.1.114027.200.3.10.7.3 |
| 2.16.840.1.114027.200.3.10.10.1.4 | id-emspki-nfssp-medium-hardware| 2.16.840.1.114027.200.3.10.7.2 |
| 2.16.840.1.114027.200.3.10.10.1.6 | id-emspki-nfssp-medium-authentication | 2.16.840.1.114027.200.3.10.7.4 |
| 2.16.840.1.114027.200.3.10.10.1.6 | id-emspki-nfssp-pivi-hardware | 2.16.840.1.114027.200.3.10.7.6 |
| 2.16.840.1.114027.200.3.10.10.1.5 | id-emspki-nfssp-medium-cardAuth | 2.16.840.1.114027.200.3.10.7.5 |
| 2.16.840.1.114027.200.3.10.10.1.9 | id-emspki-nfssp-pivi-contentSigning | 2.16.840.1.114027.200.3.10.7.9 |

#### DigiCert (and former Symantec and VeriSign)

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| 2.16.840.1.114412.99.4.1.1 | DigiCert Level 1 Client Certificate - Personal | 2.16.840.1.114412.4.1.1 |
| 2.16.840.1.114412.99.4.1.2 | DigiCert Level 1 Client Certificate - Enterprise | 2.16.840.1.114412.4.1.2 |
| 2.16.840.1.114412.99.4.2 | DigiCert Level 2 Client Certificate - Basic | 2.16.840.1.114412.4.2 |
| 2.16.840.1.114412.99.4.3.1 | DigiCert Level 3 Client Certificate - US - Medium | 2.16.840.1.114412.4.3.1 |  
| 2.16.840.1.114412.99.4.3.2 | DigiCert Level 3 Client Certificate - CBP - Medium | 2.16.840.1.114412.4.3.2 |
| 2.16.840.1.114412.99.4.4.1 | Digicert Level 4 Client Certificate - US - Hardware | 2.16.840.1.114412.4.4.1 |
| 2.16.840.1.114412.99.4.4.2 | Digicert Level 4 Client Certificate - CBP - Hardware | 2.16.840.1.114412.4.4.2 |
| 2.16.840.1.113733.1.7.21.1.1 | Class 1-VTN SSP-rudimentary | 2.16.840.1.113733.1.7.23.1.1.1 |
| 2.16.840.1.113733.1.7.21.2.1 | Class 2-VTN SSP-basic | 2.16.840.1.113733.1.7.23.2.1.1 |
| 2.16.840.1.113733.1.7.21.3.6 | Class 3-VTN SSP-medium | 2.16.840.1.113733.1.7.23.3.1.6 |
| 2.16.840.1.113733.1.7.21.3.7 | Class 3-VTN SSP-mediumHardware | 2.16.840.1.113733.1.7.23.3.1.7 |
| 2.16.840.1.113733.1.7.21.3.8 | Class 3-VTN SSP-Devices | 2.16.840.1.113733.1.7.23.3.1.8 |
| 2.16.840.1.113733.1.7.21.3.13 | Class 3-VTN SSP-PIV-I Hardware | 2.16.840.1.113733.1.7.23.3.1.13 |
| 2.16.840.1.113733.1.7.21.3.14 | Class 3-VTN SSP-Medium CBP | 2.16.840.1.113733.1.7.23.3.1.14 |
| 2.16.840.1.113733.1.7.21.3.15 | Class 3-VTN SSP-Medium Hardware CBP | 2.16.840.1.113733.1.7.23.3.1.15 |
| 2.16.840.1.113733.1.7.21.3.17 | Class 3-VTN SSP-PIV-I CardAuth | 2.16.840.1.113733.1.7.23.3.1.17 |
| 2.16.840.1.113733.1.7.21.3.20 | Class 3-VTN SSP-PIV-I ContentSigning | 2.16.840.1.113733.1.7.23.3.1.20 |

### Commercial PKI Bridge Test OIDs

#### SAFE Bio-Pharma Bridge

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| N/A | Safe basic | 1.3.6.1.4.1.23165.1.1 |
| N/A | Safe med software | 1.3.6.1.4.1.23165.1.2 |
| N/A | Safe med HW | 1.3.6.1.4.1.23165.1.3 |

#### CertiPath Bridge

| Test OID                    | Policy                 | Production OID     |
| --------------------------- | ---------------------- | ------------------ |
| 1.3.6.1.4.1.24019.1.1.1.101 | CertiPath medium Software | 1.3.6.1.4.1.24019.1.1.1.1 |
| 1.3.6.1.4.1.24019.1.1.1.102 | CertiPath medium Hardware | 1.3.6.1.4.1.24019.1.1.1.2 |
| 1.3.6.1.4.1.24019.1.1.1.103 | CertiPath highHardware | 1.3.6.1.4.1.24019.1.1.1.3 |
| 1.3.6.1.4.1.24019.1.1.1.104 | CertiPath medium CBP Software | 1.3.6.1.4.1.24019.1.1.1.4 |
| 1.3.6.1.4.1.24019.1.1.1.105 | CertiPath medium CBP Hardware | 1.3.6.1.4.1.24019.1.1.1.5 |
| 1.3.6.1.4.1.24019.1.1.1.106 | CertiPath highCBPHardware | 1.3.6.1.4.1.24019.1.1.1.6 |
| 1.3.6.1.4.1.24019.1.1.1.107 | CertiPath IceCAP-hardware | 1.3.6.1.4.1.24019.1.1.1.7 |
| 1.3.6.1.4.1.24019.1.1.1.108 | CertiPath IceCAP-cardAuth | 1.3.6.1.4.1.24019.1.1.1.8 |
| 1.3.6.1.4.1.24019.1.1.1.109 | CertiPath IceCAP-contentSigning | 1.3.6.1.4.1.24019.1.1.1.9 |
| 1.3.6.1.4.1.24019.1.1.1.110 | CertiPath variant medium Software | 1.3.6.1.4.1.24019.1.1.1.17 |
| 1.3.6.1.4.1.24019.1.1.1.111 | CertiPath variant medium Hardware | 1.3.6.1.4.1.24019.1.1.1.18 |
| 1.3.6.1.4.1.24019.1.1.1.112 | CertiPath variant high Hardware | 1.3.6.1.4.1.24019.1.1.1.19 |
| 1.3.6.1.4.1.24019.1.1.1.113 | CertiPath variant medium CBP Software | 1.3.6.1.4.1.24019.1.1.1.20 |
| 1.3.6.1.4.1.24019.1.1.1.114 | CertiPath variant medium CBP Hardware | 1.3.6.1.4.1.24019.1.1.1.21 |
| 1.3.6.1.4.1.24019.1.1.1.115 | CertiPath variant high CBP Hardware | 1.3.6.1.4.1.24019.1.1.1.22 |