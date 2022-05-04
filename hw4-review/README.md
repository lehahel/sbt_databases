# Prometheus

## 1. History of development
 - Created in 2012 by *Soundcloud*
 - Open-source
 - TimeSeries database
 - Became a system monitoring standard

## 2. Tools to interact with DB
 - HTTP queries
 - Web-interface
 - Pushgateway (software to push metrics to prometheus)
 - Custom exporters for app
 - Grafana and other tools for metrics visualization

## 3. Database engine
 - Uses own database engine

## 4. Queries in database
  ### Main facts:
   - Uses **PromQL** (Prometheus Query Language)
  - Allows only to get information
  ### Example
  1. I pushed metrics to Prometheus using **Pushgateway**:

    echo "some_metric 99" | curl --data-binary @- http://0.0.0.0:9091/metrics/job/some_job

    echo "cpu_temperature 75" | curl --data-binary @- http://0.0.0.0:9091/metrics/job/some_job

    echo 'one_more_metric{label="label1"} 45' | curl --data-binary @- http://0.0.0.0:9091/metrics/job/some_job

  2. Got metric:

    some_metric
    --> some_metric { job="some_job" } 99
  3. Got metric with filter:

    some_metric { job="some_job" }
    --> some_metric { job="some_job" } 99
  4. Got metric by tag

    { label="label1" }
    --> one_more_metric { job="some_job", label="label1" } 45
  5. As we see, queries are pretty simple

## 5. Database files distribution over different carriers
 - Local storage
 - Custom third-party storage using adapter

## 6. Programming language used
 - Go

## 7. Indexes
 - No

## 8. Queries execution process
 - Takes metric name and finds metrics which match filter

## 9. Query plan
 - No

## 10. Transactions
 - No

## 11. Restoring methods
 - Restoring from snapshot

## 12. Sharding
 - Horizontal sharding
 - Usually used for dividing different collections of metrics (and for perfomance, too)

## 13. Data mining, data warehousing, OLAP
 - It is not about Prometheus, it does not store data important for business

## 14. Security
 - Server-side authentification, authorization and encryption will be available in the future
 - All the data can be got by curl without authentification

## 15. Community
 - Prometheus is open-source, so anyone can contribute
 - No company controls the product

## 16. Data for database demonstration
 - check data.txt

## 17. Demo database
 - https://demo.do.prometheus.io

## 18. Documentation and examples
 - https://prometheus.io

## 19. Information and updates
 - #prometheus at https://libera.chat