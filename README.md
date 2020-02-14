# mule4-max_concurrency_poc
A Mulesoft 4.x project to test flow max concurrency

This was created as a proof that there is an issue with Mule Runtime v4.2.2 not honoring max concurrency for flows. 

The "waitFlow" in the max_concurrency_poc.xml is configured with maxConcurrency="1".

If this project is run using Mule Runtime 4.2.1 (v7.3.3.201911131613), then the log will show that only one instance of waitFlow will execute at a time. If one of the schedulers calls waitFlow while there is already an instance of waitFlow executing, then it will queue and execution will begin within a few milliseconds of the completion of the executing instance.

If this project is run using Mule Runtime 4.2.2 (v7.3.5.201911202039), the log will show new instances of waitFlow will start without regard to any currently executing instances.
