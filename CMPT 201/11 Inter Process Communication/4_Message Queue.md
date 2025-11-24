

## Message Queue
- Similar to [[3_FIFO|FIFO]], but used to send **full structured data** at once, instead of a byte stream
- A message is a **struct** or a **union**
- The queue is a **priority queue**, where messages are sent based on their priority, or FIFO if priorities are the same

### Sending a message
`mq_send` synopsis:
```c
#include <mqueue.h>
int mq_send(mqd_t mqdes, char *msg_ptr, size_t msg_len, unsigned int msg_prio);
```

In the function prototype:
- `msg_ptr` is the pointer to the structured data
- `msg_prio` is the priority of the message

### Receiving a message
`mq_receive` synopsis:
```c
#include <mqueue.h>
ssize_t mq_receive(mqd_t mqdes, char *msg_ptr, size_t msg_len, unsigned int *msg_prio);
```

`mq_receive` retrieves the **oldest highest priority** message, the entire message at once.

