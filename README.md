parameter(li=83,lj=35)
integer mu(li,lj),mz(li,lj)
open(1,file='mu.txt')
open(2,file='mz.txt')
do i=1,li,2
  read(1,'(18i1)')(mu(i,j),j=1,lj,2)
end do
do i=2,li-1,2
 do j=2,lj-1,2
   muz=mu(i+1,j+1)+mu(i+1,j-1)+mu(i-1,j-1)+mu(i-1,j+1)
   if(muz.eq.4)then
    mz(i,j)=9
   else
    mz(i,j)=4-muz
   end if
   if(i.eq.li-1)then
    mz(i,j)=8
   end if
 end do
enddo
do i=2,li-1,2 
 write(2,'(17i1)')(mz(i,j),j=2,lj-1,2)
end do 
close(2)
close(1)    
end 
# tide_model
transfroming the terrain matrix
