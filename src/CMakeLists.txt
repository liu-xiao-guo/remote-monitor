cmake_minimum_required(VERSION 2.8.11)

set(AZUREIOT_INC_FOLDER ".." "/usr/include/azureiot")

include_directories(${AZUREIOT_INC_FOLDER})

set(sample_application_c_files
    ./remote_monitoring.c
)

set(sample_application_h_files
    ./remote_monitoring.h
)

add_executable(sample_app ${sample_application_c_files} ${sample_application_h_files})

target_link_libraries(sample_app
    serializer
    iothub_client
    iothub_client_amqp_transport
    aziotsharedutil
    uamqp
    pthread
    curl
    ssl
    crypto
    m
)

install(TARGETS sample_app RUNTIME DESTINATION bin)
