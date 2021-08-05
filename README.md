# Exercise 3: Build an API to allow users to interface with FIX messages

### About
For this exercise, have been provided with a raw dataset of FIX messages (If not just drop me an email). The data set, once extract should be about 1GB in size. Your task here is to first parse and ingest the messages into a suitable datastore. 

Then once that has been completed, you then need to build a simple, yet performant (read-only) RESTful API on top of the FIX message data store. The API should allows users to make HTTP requests to your service, and then respond with the correct data for a given request.

At the minimum, your service needs to implement the following API endpoints:
* **/get_msg_by_seqno(int:seqno)**
    * Expected request type: GET
    * Expected parameters: (int) seqno
        * Note about parameters: The provided parameter will be an integer specifying a sequence number of a FIX message. This field maps to the TAG=34 (or "MsgSeqNum") in the actual FIX message (see [FIX dictionary](https://www.onixs.biz/fix-dictionary/4.2/tagNum_34.html) for more info) 
    * Expected functionality: Returns single message for a requested sequence number

* **/get_msgs_by_secdesc(str:secdesc)**
    * Expected request type: GET
    * Expected parameters: (str) secdesc
        * Note about parameters: The provided parameter will be a string specifying a security description. This field maps to the TAG=107 (or "SecurityDesc") the actual FIX message (see [FIX dictionary](https://www.onixs.biz/fix-dictionary/4.2/tagNum_107.html) for more info) 
    * Expected functionality: Returns list of messages that contain requested security description

* **/get_msgs_by_sendtimerange(str:start_datetime, str:end_datetime)**
    * Expected request type: GET
    * Expected parameters: (str) start_datetime, (str) end_datetime
        * Note about parameters: The provided parameters will be strings specifying a start datetime and end datetime. This field maps to the TAG=52 (or "SendingTime") the actual FIX message (see [FIX dictionary](https://www.onixs.biz/fix-dictionary/4.2/tagNum_52.html) for more info) 
    * Expected functionality: Returns a list of messages that fall within the specified start_datetime and end_datetime



### Useful links:
* Info on the FIX protocol: https://www.fixtrading.org/what-is-fix/
* Online FIX Message parser: https://fixparser.targetcompid.com/
* Online FIX spec dictionary: https://www.onixs.biz/fix-dictionary/4.2/msgs_by_msg_type.html