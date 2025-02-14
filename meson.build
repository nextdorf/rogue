project('Rogue', 'c')

misc_conf_data = configuration_data({
  'PACKAGE_NAME': meson.project_name(),
  'PACKAGE_TARNAME': 'rogue',
  'PACKAGE_VERSION': '5.4.4',
  'PACKAGE_STRING': 'Rogue 5.4.4',
  'PACKAGE_BUGREPORT': 'yendor@rogueforge.net',

  'PROGRAM': 'rogue',

  'GROFF': 'groff',
  'NROFF': 'nroff',
  'TBL': 'tbl',
  'COLCRT': 'colcrt',
  'SED': 'sed',
  'SCOREFILE': 'rogue.scr',
  'LOCKFILE': 'rogue.lck',
  'GROUPOWNER': '',
  # 'TARGET': 'x86_64-unknown-linux-gnu'
  'TARGET': '@0@-@1@'.format(target_machine.cpu(), target_machine.system()), #TODO: Check if this is OK like this
})

main_conf_data = configuration_data({
  # Define if scorefile is top scores, not top players
  'ALLSCORES': 1,

  # Define if checktime feature should be enabled
  # 'CHECKTIME': false,

  # Define to group owner of setgid executable
  # 'GROUPOWNER': false,

  # Define to 1 if you have the `alarm' function.
  'HAVE_ALARM': 1,

  # Define to 1 if you have the <arpa/inet.h> header file.
  'HAVE_ARPA_INET_H': 1,

  # Define to 1 if libcurses is requested
  'HAVE_CURSES_H': 1,

  # Define to 1 if you don't have `vprintf' but do have `_doprnt.'
  # 'HAVE_DOPRNT': false,

  # Define to 1 if you have the `erasechar' function.
  'HAVE_ERASECHAR': 1,

  # Define if ncurses has ESCDELAY variable
  'HAVE_ESCDELAY': 1,

  # Define to 1 if you have the <fcntl.h> header file.
  'HAVE_FCNTL_H': 1,

  # Define to 1 if you have the `fork' function.
  'HAVE_FORK': 1,

  # Define to 1 if you have the `getgid' function.
  'HAVE_GETGID': 1,

  # Define to 1 if you have the `getloadavg' function.
  'HAVE_GETLOADAVG': 1,

  # Define to 1 if you have the `getpass' function.
  'HAVE_GETPASS': 1,

  # Define to 1 if you have the `getpwuid' function.
  'HAVE_GETPWUID': 1,

  # Define to 1 if you have the `getuid' function.
  'HAVE_GETUID': 1,

  # Define to 1 if you have the <inttypes.h> header file.
  'HAVE_INTTYPES_H': 1,

  # Define to 1 if you have the `killchar' function.
  'HAVE_KILLCHAR': 1,

  # Define to 1 if you have the <limits.h> header file.
  'HAVE_LIMITS_H': 1,

  # Define to 1 if you have the `loadav' function.
  # 'HAVE_LOADAV': false,

  # Define to 1 if `lstat' has the bug that it succeeds when given the
  # zero-length file name argument.
  # 'HAVE_LSTAT_EMPTY_STRING_BUG': false,

  # Define to 1 if you have the <memory.h> header file.
  'HAVE_MEMORY_H': 1,

  # Define to 1 if you have the `memset' function.
  'HAVE_MEMSET': 1,

  # Define to 1 if libncurses is requested
  # 'HAVE_NCURSES_H': false,

  # Define to 1 if you have the <ncurses/term.h> header file.
  # 'HAVE_NCURSES_TERM_H': false,

  # Define to 1 if you have the `nlist' function.
  # 'HAVE_NLIST': false,

  # Define to 1 if you have the <nlist.h> header file.
  'HAVE_NLIST_H': 1,

  # Define to 1 if you have the <process.h> header file.
  # 'HAVE_PROCESS_H': false,

  # Define to 1 if you have the <pwd.h> header file.
  'HAVE_PWD_H': 1,

  # Define to 1 if you have the `setenv' function.
  'HAVE_SETENV': 1,

  # Define to 1 if you have the `setgid' function.
  'HAVE_SETGID': 1,

  # Define to 1 if you have the `setregid' function.
  'HAVE_SETREGID': 1,

  # Define to 1 if you have the `setresgid' function.
  'HAVE_SETRESGID': 1,

  # Define to 1 if you have the `setresuid' function.
  'HAVE_SETRESUID': 1,

  # Define to 1 if you have the `setreuid' function.
  'HAVE_SETREUID': 1,

  # Define to 1 if you have the `setuid' function.
  'HAVE_SETUID': 1,

  # Define to 1 if you have the `spawnl' function.
  # 'HAVE_SPAWNL': false,

  # Define to 1 if `stat' has the bug that it succeeds when given the
  # zero-length file name argument.
  # 'HAVE_STAT_EMPTY_STRING_BUG': false,

  # Define to 1 if stdbool.h conforms to C99.
  'HAVE_STDBOOL_H': 1,

  # Define to 1 if you have the <stdint.h> header file.
  'HAVE_STDINT_H': 1,

  # Define to 1 if you have the <stdlib.h> header file.
  'HAVE_STDLIB_H': 1,

  # Define to 1 if you have the `strchr' function.
  'HAVE_STRCHR': 1,

  # Define to 1 if you have the `strerror' function.
  'HAVE_STRERROR': 1,

  # Define to 1 if you have the <strings.h> header file.
  'HAVE_STRINGS_H': 1,

  # Define to 1 if you have the <string.h> header file.
  'HAVE_STRING_H': 1,

  # Define to 1 if you have the <sys/ioctl.h> header file.
  'HAVE_SYS_IOCTL_H': 1,

  # Define to 1 if you have the <sys/stat.h> header file.
  'HAVE_SYS_STAT_H': 1,

  # Define to 1 if you have the <sys/types.h> header file.
  'HAVE_SYS_TYPES_H': 1,

  # Define to 1 if you have the <sys/utsname.h> header file.
  'HAVE_SYS_UTSNAME_H': 1,

  # Define to 1 if you have the <termios.h> header file.
  'HAVE_TERMIOS_H': 1,

  # Define to 1 if you have the <term.h> header file.
  'HAVE_TERM_H': 1,

  # Define to 1 if you have the <unistd.h> header file.
  'HAVE_UNISTD_H': 1,

  # Define to 1 if you have the <utmp.h> header file.
  'HAVE_UTMP_H': 1,

  # Define to 1 if you have the `vfork' function.
  'HAVE_VFORK': 1,

  # Define to 1 if you have the <vfork.h> header file.
  # 'HAVE_VFORK_H': false,

  # Define to 1 if you have the `vprintf' function.
  'HAVE_VPRINTF': 1,

  # Define to 1 if `fork' works.
  'HAVE_WORKING_FORK': 1,

  # Define to 1 if `vfork' works.
  'HAVE_WORKING_VFORK': 1,

  # Define to 1 if the system has the type `_Bool'.
  'HAVE__BOOL': 1,

  # Define to 1 if you have the `_spawnl' function.
  # 'HAVE__SPAWNL': false,

  # define if we should use program's load average function instead of system
    
  # 'LOADAV': false,

  # Define to file to use for scoreboard lockfile
  'LOCKFILE': '"@0@"'.format(misc_conf_data.get('LOCKFILE')),

  # Define to 1 if `lstat' dereferences a symlink specified with a trailing
  # slash.
  'LSTAT_FOLLOWS_SLASHED_SYMLINK': 1,

  # Define to include wizard mode
  # 'MASTER': false,

  # Define if maxusers feature should be enabled
  # 'MAXLOAD': false,

  # Define if maxusers feature should be enabled
  # 'MAXUSERS': false,

  # kernel file to pass to nlist() when reading load average (unlikely to work)
    
  # 'NAMELIST': false,

  # word for the number of scores to store in scoreboard
  'NUMNAME': '"TEN"',

  # number of scores to store in scoreboard
  'NUMSCORES': 10,

  # Define to the address where bug reports for this package should be sent.
  'PACKAGE_BUGREPORT': '"@0@"'.format(misc_conf_data.get('PACKAGE_BUGREPORT')),

  # Define to the full name of this package.
  'PACKAGE_NAME': '"@0@"'.format(misc_conf_data.get('PACKAGE_NAME')),

  # Define to the full name and version of this package.
  'PACKAGE_STRING': '"@0@"'.format(misc_conf_data.get('PACKAGE_STRING')),

  # Define to the one symbol short name of this package.
  'PACKAGE_TARNAME': '"@0@"'.format(misc_conf_data.get('PACKAGE_TARNAME')),

  # Define to the version of this package.
  'PACKAGE_VERSION': '"@0@"'.format(misc_conf_data.get('PACKAGE_VERSION')),

  # Define crypt(3) wizard mode password
  # 'PASSWD': false,

  # Define as the return type of signal handlers (`int' or `void').
  'RETSIGTYPE': 'void',

  # Define to file to use for scoreboard
  'SCOREFILE': '"@0@"'.format(misc_conf_data.get('SCOREFILE')),

  # Define to 1 if you have the ANSI C header files.
  'STDC_HEADERS': 1,

  # Define to 1 if your <sys/time.h> declares `struct tm'.
  # 'TM_IN_SYS_TIME': false,

  # define if we should use program's user counting function instead of
  # system's
  # 'UCOUNT': false,

  # utmp like file to pass to ucount() when counting online users (unlikely to
  # work)
  # 'UTMP': false,

  # Define to empty if `const' does not conform to ANSI C.
  # 'const': false,

  # Define to `int' if <sys/types.h> doesn't define.
  # 'gid_t': false,

  # Define to `int' if <sys/types.h> does not define.
  # 'pid_t': false,

  # Define to `unsigned int' if <sys/types.h> does not define.
  # 'size_t': false,

  # Define to `int' if <sys/types.h> doesn't define.
  # 'uid_t': false,

  # Define as `fork' if `vfork' does not work.
  # 'vfork': false,
})


# configure_file(input: 'Makefile.in', output: 'Makefile', configuration: misc_conf_data)
configure_file(input: 'rogue.6.in', output: 'rogue.6', configuration: misc_conf_data)
configure_file(input: 'rogue.cat.in', output: 'rogue.cat', configuration: misc_conf_data)
configure_file(input: 'rogue.doc.in', output: 'rogue.doc', configuration: misc_conf_data)
configure_file(input: 'rogue.html.in', output: 'rogue.html', configuration: misc_conf_data)
configure_file(input: 'rogue.me.in', output: 'rogue.me', configuration: misc_conf_data)

configure_file(output: 'config.h', configuration: main_conf_data)

# deps = dependency('ncursesw')
# deps = dependency('ncurses')
deps = dependency('curses')

add_project_arguments(['-DHAVE_CONFIG_H'], language: 'cpp')

source_files = files(
  'vers.c', 'extern.c', 'armor.c', 'chase.c', 'command.c', 'daemon.c', 'daemons.c', 'fight.c',
  'init.c', 'io.c', 'list.c', 'mach_dep.c', 'main.c', 'mdport.c', 'misc.c', 'monsters.c', 'move.c',
  'new_level.c', 'options.c', 'pack.c', 'passages.c', 'potions.c', 'rings.c', 'rip.c', 'rooms.c',
  'save.c', 'scrolls.c', 'state.c', 'sticks.c', 'things.c', 'weapons.c', 'wizard.c', 'xcrypt.c')

# misc_source_files = files('findpw.c', 'scedit.c', 'scmisc.c')

executable(misc_conf_data.get('PROGRAM'), sources: source_files, dependencies : deps)
