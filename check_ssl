#!/bin/bash
# check_ssl v1.0

# variables 
cert=$1
_now_epoch=$(date +%s)

if [ -z "$cert" ]
then
echo 'You need to include .pem file with path'
exit
else
# do time calc of cert exp dates & print if warn
_ssl_exp=$(openssl x509 -enddate -noout -in "$cert" | awk -F '=' '{print $2}');
_ssl_exp_epoch=$( date -d "$_ssl_exp" +%s );
_expiry_days="$((($_ssl_exp_epoch - $_now_epoch) / (3600 * 24)))";
if [[ "$_expiry_days" -lt "1000" ]]
then
echo "Warning: $cert expires in $_expiry_days days"
fi
fi

