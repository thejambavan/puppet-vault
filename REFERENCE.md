# Reference

<!-- DO NOT EDIT: This document was generated by Puppet Strings -->

## Table of Contents

### Classes

#### Public Classes

* [`openbao`](#openbao): install openbao

#### Private Classes

* `openbao::config`: This class is called from openbao for service config
* `openbao::install`
* `openbao::params`: This class is meant to be called from openbao. It sets variables according to platform.
* `openbao::service`

## Classes

### <a name="openbao"></a>`openbao`

install openbao

#### Parameters

The following parameters are available in the `openbao` class:

* [`user`](#-openbao--user)
* [`manage_user`](#-openbao--manage_user)
* [`group`](#-openbao--group)
* [`manage_group`](#-openbao--manage_group)
* [`bin_dir`](#-openbao--bin_dir)
* [`config_dir`](#-openbao--config_dir)
* [`config_mode`](#-openbao--config_mode)
* [`purge_config_dir`](#-openbao--purge_config_dir)
* [`download_url`](#-openbao--download_url)
* [`download_url_base`](#-openbao--download_url_base)
* [`download_extension`](#-openbao--download_extension)
* [`service_name`](#-openbao--service_name)
* [`service_provider`](#-openbao--service_provider)
* [`service_options`](#-openbao--service_options)
* [`manage_repo`](#-openbao--manage_repo)
* [`manage_service`](#-openbao--manage_service)
* [`num_procs`](#-openbao--num_procs)
* [`api_addr`](#-openbao--api_addr)
* [`version`](#-openbao--version)
* [`extra_config`](#-openbao--extra_config)
* [`enable_ui`](#-openbao--enable_ui)
* [`arch`](#-openbao--arch)
* [`os`](#-openbao--os)
* [`manage_download_dir`](#-openbao--manage_download_dir)
* [`download_dir`](#-openbao--download_dir)
* [`package_ensure`](#-openbao--package_ensure)
* [`package_name`](#-openbao--package_name)
* [`install_method`](#-openbao--install_method)
* [`manage_file_capabilities`](#-openbao--manage_file_capabilities)
* [`disable_mlock`](#-openbao--disable_mlock)
* [`max_lease_ttl`](#-openbao--max_lease_ttl)
* [`default_lease_ttl`](#-openbao--default_lease_ttl)
* [`telemetry`](#-openbao--telemetry)
* [`disable_cache`](#-openbao--disable_cache)
* [`seal`](#-openbao--seal)
* [`ha_storage`](#-openbao--ha_storage)
* [`listener`](#-openbao--listener)
* [`manage_storage_dir`](#-openbao--manage_storage_dir)
* [`storage`](#-openbao--storage)
* [`manage_service_file`](#-openbao--manage_service_file)
* [`service_ensure`](#-openbao--service_ensure)
* [`service_enable`](#-openbao--service_enable)
* [`manage_config_file`](#-openbao--manage_config_file)
* [`download_filename`](#-openbao--download_filename)
* [`manage_config_dir`](#-openbao--manage_config_dir)

##### <a name="-openbao--user"></a>`user`

Data type: `Any`

Customise the user openbao runs as, will also create the user unless `manage_user` is false.

Default value: `'openbao'`

##### <a name="-openbao--manage_user"></a>`manage_user`

Data type: `Any`

Whether or not the module should create the user.

Default value: `true`

##### <a name="-openbao--group"></a>`group`

Data type: `Any`

Customise the group openbao runs as, will also create the user unless `manage_group` is false.

Default value: `'openbao'`

##### <a name="-openbao--manage_group"></a>`manage_group`

Data type: `Any`

Whether or not the module should create the group.

Default value: `true`

##### <a name="-openbao--bin_dir"></a>`bin_dir`

Data type: `Any`

Directory the openbao executable will be installed in.

Default value: `$openbao::params::bin_dir`

##### <a name="-openbao--config_dir"></a>`config_dir`

Data type: `Any`

Directory the openbao configuration will be kept in.

Default value: `if $install_method == 'repo' and $manage_repo { '/etc/openbao.d' } else { '/etc/openbao'`

##### <a name="-openbao--config_mode"></a>`config_mode`

Data type: `Any`

Mode of the configuration file (config.json). Defaults to '0750'

Default value: `'0750'`

##### <a name="-openbao--purge_config_dir"></a>`purge_config_dir`

Data type: `Any`

Whether the `config_dir` should be purged before installing the generated config.

Default value: `true`

##### <a name="-openbao--download_url"></a>`download_url`

Data type: `Any`

Manual URL to download the openbao zip distribution from.

Default value: `undef`

##### <a name="-openbao--download_url_base"></a>`download_url_base`

Data type: `Any`

Base URL to download openbao zip distribution from.

Default value: `'https://github.com/openbao/openbao/releases/download/'`

##### <a name="-openbao--download_extension"></a>`download_extension`

Data type: `Any`

The extension of the openbao download

Default value: `'zip'`

##### <a name="-openbao--service_name"></a>`service_name`

Data type: `Any`

Customise the name of the system service

Default value: `'openbao'`

##### <a name="-openbao--service_provider"></a>`service_provider`

Data type: `Any`

Customise the name of the system service provider; this
also controls the init configuration files that are installed.

Default value: `$facts['service_provider']`

##### <a name="-openbao--service_options"></a>`service_options`

Data type: `Any`

Extra argument to pass to `openbao server`, as per: `openbao server --help`

Default value: `''`

##### <a name="-openbao--manage_service"></a>`manage_service`

Data type: `Any`

Instruct puppet to manage service or not

Default value: `true`

##### <a name="-openbao--num_procs"></a>`num_procs`

Data type: `Any`

Sets the GOMAXPROCS environment variable, to determine how many CPUs openbao
can use. The official openbao Terraform install.sh script sets this to the
output of ``nprocs``, with the comment, "Make sure to use all our CPUs,
because openbao can block a scheduler thread". Default: number of CPUs
on the system, retrieved from the ``processorcount`` Fact.

Default value: `$facts['processors']['count']`

##### <a name="-openbao--api_addr"></a>`api_addr`

Data type: `Optional[String]`

Specifies the address (full URL) to advertise to other openbao servers in the
cluster for client redirection. This value is also used for plugin backends.
This can also be provided via the environment variable openbao_API_ADDR. In
general this should be set as a full URL that points to the value of the
listener address

Default value: `undef`

##### <a name="-openbao--version"></a>`version`

Data type: `Any`

The version of openbao to install

Default value: `'1.12.0'`

##### <a name="-openbao--extra_config"></a>`extra_config`

Data type: `Hash`



Default value: `{}`

##### <a name="-openbao--enable_ui"></a>`enable_ui`

Data type: `Optional[Boolean]`



Default value: `undef`

##### <a name="-openbao--arch"></a>`arch`

Data type: `Any`



Default value: `$openbao::params::arch`

##### <a name="-openbao--os"></a>`os`

Data type: `Any`



Default value: `downcase($facts['kernel'])`

##### <a name="-openbao--manage_download_dir"></a>`manage_download_dir`

Data type: `Any`



Default value: `false`

##### <a name="-openbao--download_dir"></a>`download_dir`

Data type: `Any`



Default value: `'/tmp'`

##### <a name="-openbao--package_ensure"></a>`package_ensure`

Data type: `Any`



Default value: `'installed'`

##### <a name="-openbao--package_name"></a>`package_name`

Data type: `Any`



Default value: `'openbao'`

##### <a name="-openbao--install_method"></a>`install_method`

Data type: `Any`



Default value: `$openbao::params::install_method`

##### <a name="-openbao--manage_file_capabilities"></a>`manage_file_capabilities`

Data type: `Any`



Default value: `undef`

##### <a name="-openbao--disable_mlock"></a>`disable_mlock`

Data type: `Any`



Default value: `undef`

##### <a name="-openbao--max_lease_ttl"></a>`max_lease_ttl`

Data type: `Optional[String]`



Default value: `undef`

##### <a name="-openbao--default_lease_ttl"></a>`default_lease_ttl`

Data type: `Optional[String]`



Default value: `undef`

##### <a name="-openbao--telemetry"></a>`telemetry`

Data type: `Optional[Hash]`



Default value: `undef`

##### <a name="-openbao--disable_cache"></a>`disable_cache`

Data type: `Optional[Boolean]`



Default value: `undef`

##### <a name="-openbao--seal"></a>`seal`

Data type: `Optional[Hash]`



Default value: `undef`

##### <a name="-openbao--ha_storage"></a>`ha_storage`

Data type: `Optional[Hash]`



Default value: `undef`

##### <a name="-openbao--listener"></a>`listener`

Data type: `Variant[Hash, Array[Hash]]`



Default value: `{ 'tcp' => { 'address' => '127.0.0.1:8200', 'tls_disable' => 1 }, }`

##### <a name="-openbao--manage_storage_dir"></a>`manage_storage_dir`

Data type: `Any`



Default value: `false`

##### <a name="-openbao--storage"></a>`storage`

Data type: `Hash`



Default value: `{ 'file' => { 'path' => '/var/lib/openbao' } }`

##### <a name="-openbao--manage_service_file"></a>`manage_service_file`

Data type: `Optional[Boolean]`



Default value: `$openbao::params::manage_service_file`

##### <a name="-openbao--service_ensure"></a>`service_ensure`

Data type: `Any`



Default value: `'running'`

##### <a name="-openbao--service_enable"></a>`service_enable`

Data type: `Any`



Default value: `true`

##### <a name="-openbao--manage_config_file"></a>`manage_config_file`

Data type: `Any`



Default value: `true`

##### <a name="-openbao--download_filename"></a>`download_filename`

Data type: `Any`



Default value: `'openbao.zip'`

##### <a name="-openbao--manage_config_dir"></a>`manage_config_dir`

Data type: `Boolean`

enable/disable the directory management. not required for package based installations

Default value: `$install_method == 'archive'`

