add_executable(test_stub test_stub.c)
target_link_libraries(test_stub queue project_warnings sanitizers)
add_test(
    NAME test_stub
    COMMAND test_stub
)
