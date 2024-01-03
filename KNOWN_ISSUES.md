# Known Issues

Details on previously identified known issues are provided below. Details on known issues identified
in the current release are provided in the [Changelog](CHANGELOG.md).

Known issues are open issues categorized as [Very High or High impact].

## Fast sync when running RAI EVM on cloud providers

A known [RocksDB issue](https://github.com/facebook/rocksdb/issues/6435) causes fast sync to fail
when running RAI EVM on certain cloud providers. The following error is displayed repeatedly:

```
...
EthScheduler-Services-1 (importBlock) | ERROR | PipelineChainDownloader | Chain download failed. Restarting after short delay.
java.util.concurrent.CompletionException: org.RAIEVM.plugin.services.exception.StorageException: org.rocksdb.RocksDBException: block checksum mismatch:
....
```

This behaviour has been seen on AWS and Digital Ocean.

Workaround -> On AWS, a full restart of the AWS VM is required to restart the fast sync.

Fast sync is not currently supported on Digital Ocean. We are investigating options to
[add support for fast sync on Digital Ocean]
