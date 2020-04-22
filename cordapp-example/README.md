
# TDH

## Intro
Share KYC records. And more.

## Setup

Dependencies: 
- Gradle: Just use the Gradle-Wrapper (./gradlew) and try to build the project, things will be handled for you. Unless 
you happen to be an unlucky user of a Swiss-Post Windows machine which basically blocks everything. Good luck. 
(I uploaded some Corda-Deps to Artifactory, so you might actually have a chance)
- JDK: Make sure to downgrade to Java 8

## Test
- UnitTests: LedgerDSL. Test the flow and contract logic. Run by Gradle "test" task.
- IntegrationTests: DriverDSL Tests. Runs tests against local nodes. Run by "integrationTest" Gradle task.


## Running
Available nodes-types to run:
- ROU: Regional operating unit - Issuance of KYC records
- Master/Notary: Gets metadata of all transactions to be able to search for records.
- Bank: The ones who actually need the KYC records.
- Observer: Also just sees metadata of transactions.
    
Run Gradle task "deployNodes". After that start nodes by executing "runnodes" in the build directory.

To run nodes individually, run the corda.jar in the corresponding node directory.

Frontends:
Start the Apps which are providing RPC and frontend services. Then start the Angular UIs.

## Terminal

Run flows directly on nodes (example):

> flow start Allocation ccdId: 12345, corporateName: "Name-1", corporateLei: "Corporate-Lei"
