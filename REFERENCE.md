# Reference
<!-- DO NOT EDIT: This document was generated by Puppet Strings -->

## Resource types

* [`zfs`](#zfs): Manage zfs. Create destroy and set properties on zfs instances.  **Autorequires:** If Puppet is managing the zpool at the root of this zfs in
* [`zpool`](#zpool): Manage zpools. Create and delete zpools. The provider WILL NOT SYNC, only report differences.  Supports vdevs with mirrors, raidz, logs and s

## Resource types

### zfs

Manage zfs. Create destroy and set properties on zfs instances.

**Autorequires:** If Puppet is managing the zpool at the root of this zfs
instance, the zfs resource will autorequire it. If Puppet is managing any
parent zfs instances, the zfs resource will autorequire them.

#### Examples

##### Using zfs.

```puppet
zfs { 'tstpool':
  ensure => present,
}
```

#### Properties

The following properties are available in the `zfs` type.

##### `ensure`

Valid values: present, absent

The basic property that the resource should be in.

Default value: present

##### `aclinherit`

The aclinherit property. Valid values are `discard`, `noallow`, `restricted`, `passthrough`, `passthrough-x`.

##### `aclmode`

The aclmode property. Valid values are `discard`, `groupmask`, `passthrough`.

##### `acltype`

The acltype propery. Valid values are 'noacl' and 'posixacl'. Only supported on Linux.

##### `atime`

The atime property. Valid values are `on`, `off`.

##### `canmount`

The canmount property. Valid values are `on`, `off`, `noauto`.

##### `checksum`

The checksum property. Valid values are `on`, `off`, `fletcher2`, `fletcher4`, `sha256`.

##### `compression`

The compression property. Valid values are `on`, `off`, `lzjb`, `gzip`, `gzip-[1-9]`, `zle`.

##### `copies`

The copies property. Valid values are `1`, `2`, `3`.

##### `dedup`

The dedup property. Valid values are `on`, `off`.

##### `devices`

The devices property. Valid values are `on`, `off`.

##### `exec`

The exec property. Valid values are `on`, `off`.

##### `logbias`

The logbias property. Valid values are `latency`, `throughput`.

##### `mountpoint`

The mountpoint property. Valid values are `<path>`, `legacy`, `none`.

##### `nbmand`

The nbmand property. Valid values are `on`, `off`.

##### `primarycache`

The primarycache property. Valid values are `all`, `none`, `metadata`.

##### `quota`

The quota property. Valid values are `<size>`, `none`.

##### `readonly`

The readonly property. Valid values are `on`, `off`.

##### `recordsize`

The recordsize property. Valid values are powers of two between 512 and 128k.

##### `refquota`

The refquota property. Valid values are `<size>`, `none`.

##### `refreservation`

The refreservation property. Valid values are `<size>`, `none`.

##### `reservation`

The reservation property. Valid values are `<size>`, `none`.

##### `secondarycache`

The secondarycache property. Valid values are `all`, `none`, `metadata`.

##### `setuid`

The setuid property. Valid values are `on`, `off`.

##### `shareiscsi`

The shareiscsi property. Valid values are `on`, `off`, `type=<type>`.

##### `sharenfs`

The sharenfs property. Valid values are `on`, `off`, share(1M) options

##### `sharesmb`

The sharesmb property. Valid values are `on`, `off`, sharemgr(1M) options

##### `snapdir`

The snapdir property. Valid values are `hidden`, `visible`.

##### `version`

The version property. Valid values are `1`, `2`, `3`, `4`, `current`.

##### `volsize`

The volsize property. Valid values are `<size>`

##### `vscan`

The vscan property. Valid values are `on`, `off`.

##### `xattr`

The xattr property. Valid values are `on`, `off`.

##### `zoned`

The zoned property. Valid values are `on`, `off`.

#### Parameters

The following parameters are available in the `zfs` type.

##### `name`

namevar

The full name for this filesystem (including the zpool).

### zpool

Manage zpools. Create and delete zpools. The provider WILL NOT SYNC, only report differences.

Supports vdevs with mirrors, raidz, logs and spares.

#### Examples

##### Using zpool.

```puppet
zpool { 'tstpool':
  ensure => present,
  disk => '/ztstpool/dsk',
}
```

#### Properties

The following properties are available in the `zpool` type.

##### `ensure`

Valid values: present, absent

The basic property that the resource should be in.

Default value: present

##### `disk`

The disk(s) for this pool. Can be an array or a space separated string.

##### `mirror`

List of all the devices to mirror for this pool. Each mirror should be a
space separated string:

    mirror => [\"disk1 disk2\", \"disk3 disk4\"],

##### `raidz`

List of all the devices to raid for this pool. Should be an array of
space separated strings:

    raidz => [\"disk1 disk2\", \"disk3 disk4\"],

##### `spare`

Spare disk(s) for this pool.

##### `log`

Log disks for this pool. This type does not currently support mirroring of log disks.

#### Parameters

The following parameters are available in the `zpool` type.

##### `pool`

namevar

The name for this pool.

##### `raid_parity`

Determines parity when using the `raidz` parameter.
