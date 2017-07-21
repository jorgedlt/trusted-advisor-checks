# trusted-advisor-checks
quasi automated trusted-advisor-checks - notes and script


 aws support describe-trusted-advisor-checks --language en \
  | grep -B2 -A2 'Amazon S3 Bucket Permissions'

            "id": "ZRxQlPsb6c",
            "name": "High Utilization Amazon EC2 Instances"

#
aws support describe-trusted-advisor-check-refresh-statuses --check-id Pfx0RwqBli
#
aws support refresh-trusted-advisor-check --check-id Pfx0RwqBli
#
aws support describe-trusted-advisor-check-result --check-id Pfx0RwqBli
#

aws support describe-trusted-advisor-check-result --check-id Pfx0RwqBli | grep -A3 metadata | egrep '\-|sbd' | tr -d '"|,'


# check tool
x () {
:
}

for i in $(cat ./accounts.cfg); do
    "$i"
    echo "$i"
    #
    aws support describe-trusted-advisor-check-refresh-statuses --check-id Pfx0RwqBli > /dev/null
    #
    aws support refresh-trusted-advisor-check --check-id Pfx0RwqBli > /dev/null
    #
    aws support describe-trusted-advisor-check-result --check-id Pfx0RwqBli | grep -A3 metadata | egrep '\-|sbd' | egrep -v 'east|west|central' | tr -d '"|,'
done	| grep -v '\-\-'
