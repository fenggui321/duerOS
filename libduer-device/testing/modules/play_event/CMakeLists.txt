SET(TEST_DIR ${CMAKE_CURRENT_LIST_DIR}/../../..)
SET(TEST_NAME lightduer_play_event_test)

SET(TEST_FILE
    ${TEST_DIR}/testing/baidu_json_mock_functions.c
    ${TEST_DIR}/testing/mutex_mock_functions.c
    ${TEST_DIR}/modules/play_event/lightduer_play_event.c
    ${CMAKE_CURRENT_LIST_DIR}/lightduer_play_event_test.c
   )

SET(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -Wl,-T${TEST_DIR}/testing/unit_test.lds")
ADD_EXECUTABLE(${TEST_NAME} ${TEST_FILE} ${TEST_DIR}/testing/main.c)
TARGET_LINK_LIBRARIES(${TEST_NAME} cmocka)

SET(TEST_CASES
    ${TEST_CASES}
    "${CMAKE_CURRENT_BINARY_DIR}/${TEST_NAME}"
    CACHE INTERNAL
    "test cases"
    )

