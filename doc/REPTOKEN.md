## Using reptoken to pre-calculate resource tokens

When called without parameters, reptoken will create one token and output it on stderr. This is usually not what you need.

The other two modes are _directory_ and _continue_.

_Directory_ will create tokens and store them in a directory. Call:

	reptoken -outDir $Directory

This will forever create tokens and store them in `$Directory`. Repclient can use
these tokens when given the `--signdir $Directory` option. Used signer files will
be deleted by repclient.

_Continue_ will continue working on a single token and add more bits as it
can. The token will be updated and can be used concurrently by repclient. Call:

	reptoken --continue --outFile $File

For this `$File` must already exist (generated by reptoken `--outFile $File`).
Repclient can use the file using the `--signkey $File` option. The file will not
be removed by repclient.

The additional option `--minBits` modifies the target bits for collision creation.
This defines the _minimum_ bits to find, it does not constitute an upper limit.
