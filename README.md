# Ansible Role for YUM Repos

An Ansible Role for configuring PHPFPM

## Variables

Here is an example variables file

```
php:
  version: 7.1.14
  ini_config:
    php:
      engine: On
      zend.ze1_compatibility_mode: Off
      short_open_tag: On
      asp_tags: Off
      precision:  14
      y2k_compliance: On
      output_buffering: 4096
      zlib.output_compression: Off
      implicit_flush: Off
      unserialize_callback_func:
      serialize_precision: 14
      safe_mode: Off
      safe_mode_gid: Off
      safe_mode_include_dir:
      safe_mode_exec_dir:
      safe_mode_allowed_env_vars: PHP_
      safe_mode_protected_env_vars: LD_LIBRARY_PATH
      disable_functions:
      disable_classes:
      expose_php: Off
      max_execution_time: 600
      max_input_time: 60
      memory_limit: 1024M
      error_reporting:  E_ALL
      display_errors: Off
      display_startup_errors: Off
      log_errors: On
      log_errors_max_len: 1024
      ignore_repeated_errors: Off
      ignore_repeated_source: Off
      report_memleaks: On
      track_errors: Off
      error_log: /tmp/phpErrors
      variables_order: "EGPCS"
      register_globals: Off
      register_long_arrays: Off
      register_argc_argv: On
      auto_globals_jit: On
      post_max_size: 50M
      max_input_vars: 50000
      magic_quotes_gpc: Off
      magic_quotes_runtime: Off
      magic_quotes_sybase: Off
      auto_prepend_file:
      auto_append_file:
      default_mimetype: "text/html"
      always_populate_raw_post_data: -1
      doc_root:
      user_dir:
      extension_dir: "/usr/lib64/php/modules/"
      enable_dl: On
      file_uploads: On
      upload_max_filesize: 50M
      allow_url_fopen: On
      allow_url_include: Off
      default_socket_timeout: 60
      auto_detect_line_endings: On
    Date:
      date.timezone: UTC
    Syslog:
      define_syslog_variables: Off
    mail function:
      SMTP: localhost
      smtp_port: 25
      sendmail_path: /usr/sbin/sendmail -t -i
    SQL:
      sql.safe_mode: Off
    ODBC:
      odbc.allow_persistent: On
      odbc.check_persistent: On
      odbc.max_persistent: -1
      odbc.max_links: -1
      odbc.defaultlrl: 4096
      odbc.defaultbinmode: 1
    MySQL:
      mysql.allow_persistent: On
      mysql.max_persistent: -1
      mysql.max_links: -1
      mysql.default_port:
      mysql.default_socket: /var/lib/mysql/mysql.sock
      pdo_mysql.default_socket: /var/lib/mysql/mysql.sock
      mysql.default_host:
      mysql.default_user:
      mysql.default_password:
      mysql.connect_timeout: 60
      mysql.trace_mode: Off
    MySQLi:
      mysqli.max_links: -1
      mysqli.default_port: 3306
      mysqli.default_socket:
      mysqli.default_host:
      mysqli.default_user:
      mysqli.default_pw:
      mysqli.reconnect: Off
    mSQL:
      msql.allow_persistent: On
      msql.max_persistent: -1
      msql.max_links: -1
    PostgresSQL:
      pgsql.allow_persistent: On
      pgsql.auto_reset_persistent: Off
      pgsql.max_persistent: -1
      pgsql.max_links: -1
      pgsql.ignore_notice: 0
      pgsql.log_notice: 0
    Sybase:
      sybase.allow_persistent: On
      sybase.max_persistent: -1
      sybase.max_links: -1
      sybase.min_error_severity: 10
      sybase.min_message_severity: 10
      sybase.compatability_mode: Off
    Sybase-CT:
      sybct.allow_persistent: On
      sybct.max_persistent: -1
      sybct.max_links: -1
      sybct.min_server_severity: 10
      sybct.min_client_severity: 10
    bcmath:
      bcmath.scale: 0
    Informix:
      ifx.default_host:
      ifx.default_user:
      ifx.default_password:
      ifx.allow_persistent: On
      ifx.max_persistent: -1
      ifx.max_links: -1
      ifx.textasvarchar: 0
      ifx.byteasvarchar: 0
      ifx.charasvarchar: 0
      ifx.blobinfile: 0
      ifx.nullformat: 0
    Session:
      session.save_handler: files
      session.save_path: "/tmp"
      session.use_cookies: 1
      session.name: PHPSESSID
      session.auto_start: 0
      session.cookie_lifetime: 0
      session.cookie_path: /
      session.cookie_domain:
      session.cookie_httponly:
      session.serialize_handler: php
      session.gc_probability: 1
      session.gc_divisor: 1000
      session.gc_maxlifetime: 7200
      session.bug_compat_42: 0
      session.bug_compat_warn: 1
      session.referer_check:
      session.entropy_length: 0
      session.entropy_file:
      session.cache_limiter: nocache
      session.cache_expire: 180
      session.use_trans_sid: 0
      session.hash_function: 0
      session.hash_bits_per_character: 5
    #url_rewriter.tags: "a=href,area=href,frame=src,input=src,form=fakeentry"
    MSSQL:
      mssql.allow_persistent: On
      mssql.max_persistent: -1
      mssql.max_links: -1
      mssql.min_error_severity: 10
      mssql.min_message_severity: 10
      mssql.compatability_mode: Off
      mssql.secure_connection: Off
    Tidy:
      tidy.clean_output: Off
    soap:
      soap.wsdl_cache_enabled: 1
      soap.wsdl_cache_dir: "/tmp"
      soap.wsdl_cache_ttl: 86400
  fpm_config: {}

php_extensions:
  php-opcache:
    config:
      filename: 10-opcache.ini
      content:
        zend_extension: opcache.so
        opcache.enable: 1
        opcache.memory_consumption: 1024
        opcache.interned_strings_buffer: 16
        opcache.max_accelerated_files: 1000000
        opcache.revalidate_freq: 30
        opcache.fast_shutdown: 0
        opcache.blacklist_filename: /etc/php.d/opcache*.blacklist
```

## Example Task with role

```
- name: manage php-fpm installation
  hosts: kato
  roles:
    - edr.phpfpm
```
