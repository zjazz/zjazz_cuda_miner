# zjazz CUDA miner - User Manual #

## Listing  GPU devices ##

To list the available GPU devices, use the -n (or --ndevs) argument:

> zjazz_cuda -n

First column will show the device #, this is the id to reference the device when needed by other command line arguments.

## Selecting a list of GPUs to mine with

By default the miner will use all the existing devices. If you want to select a set of devices to mine with, use the argument -d (or --device) as many times as needed followed by the device #. For example, to select the #0, #2 and #5 devices:

> zjazz_cuda -d 0 -d 2 -d 5 ............

## Setting the algorithm/coin to mine ##

The algorithm/coin to mine is selected with the -a (or --algo) argument, followed by the parameter that defines the algorithm/coin for example:

> zjazz_cuda -a cuckoo ........

Here's a list of available parameters and their coin and algorithm:

| Parameter | Coin    | Algorithm |
| --------- | ------- | --------- |
| cuckoo    | Merit   | cuckoo    |
| bitcash   | BitCash | cuckoo    |

## Setting the pool to mine

To set the pool to mine the URL and username are required arguments. Also an optional password argument is allowed. Only stratum URLs are allowed.

To set the URL use  the -o (or --url) argument, to set the username use the -u (or --user) argument and to set the password use the -p (or --pass) argument.

For example, to set the pool eu.icemining.ca with the port 3333, username ABCD and the password P1:

> zjazz_cuda -o stratum+tcp://eu.icemining.ca:3333 -u ABCD -p P1 ........

## Setting more than one pool to mine (failover pool)

It is recommended to set more than one pool to mine, it will guarantee that if for some reason the connection with the pool is lost (pool down for example) the miner will automatically switch to the other pool/s.

The way to set it is as easy as adding multiple times the URL, username (and password if needed). For example, extending the example of the "Setting the pool to mine" section to use pool.merit.me with username EFGH as failover pool:

> zjazz_cuda -o stratum+tcp://eu.icemining.ca:3333 -u ABCD -o stratum+tcp://pool.merit.me:3333 -u EFGH

Note that the user argument (-u) must always follow the URL argument (-u).

Number of pools are not limited, you can set as pools as you need. Switching from one pool to the next one will always be done in a sequential order.

## Setting the number of threads per GPU

By default each GPU uses 1 mining thread. Depending on the algorithm, hashrate can be improved by using more threads per GPU. For each extra thread used the amount of GPU memory (and swap memory file size on Windows) will be incremented.

To set the number of threads for all the GPUs to a specific value use the argument -g (or --gpu-threads) followed by the number of threads to use, for example this will set to 2 the number of threads used by all the GPUs:

> zjazz_cuda -g 2 .........

To set the different number of threads per GPU device instead of a global one, use the argument to select the device (-d or --device) and after it set the threads for that device with the parameter --device-gpu-threads followed by the number of threads to be used on that device. For example, to set the number of threads for the device #0 to 2, for the device #4 to 1 and for the device  #5 to 3:

> zjazz -d 0 --device-gpu-threads 2 -d 4 --device-gpu-threads 1 -d 5 --device-gpu-threads 3

## View hashrate of each GPU device

By default, each few seconds a total hashrate message is printed to the output with the 1 minute and 10 minute hashrate averages.

Adding the argument --hashrate-per-gpu to the command line will also print the hashrate per GPU device.



