# Voting-App

### voting-app-pod
(accessed by users)
- port 80

### redis-pod 
(accessed by worker-pod and voting-app-pod)
- the voting-app saves the vote to redis database
- worker-app reads the vote from the redis db
- port 6379

### worker-app-pod
- reads count of votes from redis db and then updates that count to postgres db

### posgres-pod
(accessed by worker-pod and result-app-pod)
- worker-app updates with the total vote count
- result-app reads from it to display that vote count in browser
- port 5432

### result-app-pod
(accessed by users)
- port80