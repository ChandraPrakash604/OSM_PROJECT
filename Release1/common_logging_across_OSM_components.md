# Common logging across OSM components #

## Proposer ##
- Gerardo García (Telefónica)
- Alfonso Tierno (Telefónica)

## Type ##
**Feature**

## Target MDG/TF ##
UI, RO, SO

## Description ##
Format and log levels in all components must be uniform so that reading and debugging become easier
for end user and developer. The following is suggested:

- Each line should be prepended with date and time, in UTC or local time (to be decided).
- Log level should be included and should be coherent across modules. Typical log levels, based on
the description from [here](http://stackoverflow.com/questions/7839565/logging-levels-logback-rule-of-thumb-to-assign-log-levels "log levels"),
are:
    - **UNSET**: no logs will be shown.
    - **ERROR**: the system is in distress, customers are probably being affected (or will soon be)
    and the fix probably requires human intervention.
    - **WARNING**: an unexpected technical or business event happened, customers may be affected,
    but probably no immediate human intervention is required.
    - **INFO**: things we want to see at high volume in case we need to forensically analyze an
    issue. System lifecycle events (system start, stop) go here. "Session" lifecycle events (login,
    logout, etc.) go here. Significant boundary events should be considered as well (e.g. database
    calls, remote API calls).
    - **DEBUG**: lowest level of detail, just about everything that doesn't make the "info" cut.
- The module and function name should be included.

The specific format is to be decided. A suggestion in Python language is the following:

- datefmt="%Y-%m-%d %H:%M:%S"
- format='%(asctime)s.%(msecs)d %(levelname)s %(module)s - %(funcName)s: %(message)s'


## Demo or definition of done ##
Best practices for the different programming languages used in OSM (e.g. Python) should be
collected in a document or wiki page.

A test must be also run to check that the format is appropriate. Any test is suitable, e.g.
deployment of an NS instance, as long as it leads to ERROR and WARNING messages in all OSM
components (UI, RO and SO). While a single test for all components is desired, another possibility
is one test for each OSM component.

The log level must be set to DEBUG in all OSM components before running the test.

For each of the OSM components, the log file must be read and analyzed to find the first occurence
for each of the error messages (ERROR, WARNING, INFO and DEBUG). For each of the log levels, there
must be at least 1 occurrence, and the pattern must follow the agreed pattern.

