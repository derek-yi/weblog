    struct timespec times = {0, 0};  
    
    clock_gettime(CLOCK_MONOTONIC, &times);  
    printf("clock_gettime: %d.%d\n", times.tv_sec , times.tv_nsec/1000);  
    
    
