

//function for customer

void customer(void *arg)/*Customers Process*/
{
while(time(NULL)<end_time)
{
sem_wait(&mutex);/*P(mutex)*/
if(count<N)
{
count++;
printf("Customer:add count,count is:%d\n",count);
sem_post(&mutex);/*V(mutex)*/
sem_post(&customer);/*V(customers)*/
sem_wait(&barbers);/*P(barbers)*/
}
else
/*V(mutex)*/
/*If the number is full of customers,just put the mutex lock let go*/
sem_post(&mutex);
sleep(1);
}
}
