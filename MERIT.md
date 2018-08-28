# MERIT guide - zjazz CUDA miner #

## Mining Modes ##

### Default CPU Assistance Mode (Fastest) ###

The most optimal way to mine Merit with GPU is to use some CPU to assist the GPU with some tasks. The more GPUs used to mine, the more CPU needed.

By default *zjazz CUDA miner* uses this mode, you don't have to specify any special parameter to enable it.

### Minimum CPU  Assistance Mode ###

*zjazz CUDA miner* has a Merit mining mode where CPU time used to assist each GPU is reduced, about half CPU usage compared with the default mode. Hashrate will be lower but compared with the official Merit miner will be equal or a bit faster and will use less CPU.

To enable this mode, use the command line parameter `--cuckoo-cpu-assist-min`

### No CPU usage ###

There's another mode where no CPU is used but hashrate will drop significantly.

To enable this mode, use the command line parameter `--cuckoo-cpu-assist-disabled`

## Threads per GPU ##

By default *zjazz CUDA miner* uses 1 thread per GPU. Increasing the number of threads per GPU will improve hashrate but it will use more GPU memory and more CPU.

If possible (due the extra memory-CPU resources needed) it is recommended to use more than 1 thread per GPU, 2 threads is a good number.

To set the number of threads, use the command line paramter `-g X` where X is the number of threads. 
For example:`-g 2`

## Hashrate ##

Cuckoo is a special POW algorithm. Hashrate is measured as cycles per second.

### Edge bits ###

Depending on the historical evolution of the network difficulty, MeritCoin sets a parameter of the Cuckoo algorithm named *Edge Bits* to a specific value. For example, at the moment of writing this document *Edge Bits* is 26.

*Edge Bits* affects to the cycles/sec that a miner can achieve. The bigger *Edge Bits* is lower cycles/s can be achieved. This factor is very important when comparing hashrate between miners.

