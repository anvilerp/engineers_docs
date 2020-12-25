## How to checkout new branch that doesn't exist at my local git but exist in github .

git fetch <remote> <rbranch>:<lbranch>  
git checkout <lbranch>  

for example i want to fetch dev and am at master branch and i can't see dev at my local .

git fetch upstream dev:dev 
git checkout dev 


