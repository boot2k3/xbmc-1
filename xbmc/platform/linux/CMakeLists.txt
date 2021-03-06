set(SOURCES CPUInfoLinux.cpp
            MemUtils.cpp
            OptionalsReg.cpp
            PlatformLinux.cpp
            SysfsPath.cpp
            TimeUtils.cpp)

set(HEADERS CPUInfoLinux.h
            OptionalsReg.h
            PlatformLinux.h
            SysfsPath.h
            TimeUtils.h)

if(ALSA_FOUND)
  list(APPEND SOURCES FDEventMonitor.cpp)
  list(APPEND HEADERS FDEventMonitor.h)
endif()

if(DBUS_FOUND)
  list(APPEND SOURCES DBusMessage.cpp
                      DBusReserve.cpp
                      DBusUtil.cpp)
  list(APPEND HEADERS DBusMessage.h
                      DBusReserve.h
                      DBusUtil.h)
endif()

if("aml" IN_LIST CORE_PLATFORM_NAME_LC)
  list(APPEND SOURCES ScreenshotSurfaceAML.cpp)
  list(APPEND HEADERS ScreenshotSurfaceAML.h)
endif()

core_add_library(linuxsupport)
