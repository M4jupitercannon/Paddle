configure_file(submit_local.sh.in paddle @ONLY)

# Wheel builds run as non-root in containers; skip installing CLI script into
# the system prefix when setup.py drives the build.
if(NOT WITH_SETUP_INSTALL)
  install(
    FILES ${CMAKE_CURRENT_BINARY_DIR}/paddle
    DESTINATION bin
    PERMISSIONS
      OWNER_EXECUTE
      OWNER_WRITE
      OWNER_READ
      GROUP_EXECUTE
      GROUP_READ
      WORLD_EXECUTE
      WORLD_READ)
endif()
