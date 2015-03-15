#Code for scanning layer and producing byte 'stream'

# Introduction #

Unfinished byte stream code, uploading incase you guys need it.  If not I'll finish when I get back from Europe.


# Details #



byte getStream(LedCube c, int s){

/@Author: Samuel Dove
**@About: Trying to solve byte array problem**/


> //initialise byte stream variable
> > byte[8](8.md)[32](32.md) stream;
> > //set all bytes to 0
> > for(int i =0; i< 7; i++){
> > for(int j =0; j<31; j++){
> > > byte[i](i.md)[j](j.md)= 0x00;
> > > }
> > > }

//initialise/declare other variables

> byte thisByte;
> bit nextBit;

> int current;

//firstly loop through z-layers

> for(int z =0; z < 7; z++){

> int iterations =0;

> //bottom half of square
> if(iterations < 16){

> //loop through y, within loop of x
> for(int x = 15; x>0; x--){


> for(int y = 7; y>4; y--){
> //thisByte is the byte to be added to stream, initialise all as 0
> thisByte =0x00;
> //current knows which bit to act on
> current =0;
> //now check for green, bottom right corner
> if(x >= 9){
> > //if led is orange, both pins need to be active, hence check
> > // green and orange

> if(status[x/2][y](y.md)[z](z.md) == ORANGE || status[x/2][y](y.md)[z](z.md) == GREEN){

> //if true assign bit to 1, else leave as 0

> //current 'knows' which bit in byte to manipulate
> switch(current){
> > case(0):
> > thisByte && B00010000;
> > break;
> > case(1):
> > thisByte && B00100000;
> > break;
> > case(2):
`                         thisByte && B01000000;
> > break;
> > case(3):
> > thisByte && B10000000;
> > break;
> > }
> > //end the green/orange assignment
> > }


> }//end bottom green

> //now check for red, bottom left corner
> if(x < 9){
> if(status[x](x.md)[y](y.md)[z](z.md) == ORANGE || status[x](x.md)[y](y.md)[z](z.md) == RED){

> //current 'knows' which bit in byte to manipulate
> switch(current){
> > case(0):
> > thisByte && B00010000;
> > break;
> > case(1):
> > thisByte && B00100000;
> > break;
> > case(2):
`                         thisByte && B01000000;
> > break;
> > case(3):
> > thisByte && B10000000;
> > break;
> > }
> > //end the red/orange assignment


> }
> }
> > current++;

> }//end y
> //end bottom red

> //add thisByte to stream


> }//end x
> iterations ++;

> //end iterations for bottom half
> }




> //start iterations on top half
> if(iterations >15){

> for(int x = 15; x >0; x--){
> for(int y = 3; y > 0; y--){

> thisByte = 0x00;

> //now check for green, top right corner
> if(x >= 9){
> if(status[x/2][y](y.md)[z](z.md) == ORANGE || status[x/2][y](y.md)[z](z.md) == GREEN){







> }
> }//end top green

> //now check for red, bottom left corner
> if(x < 9){
> if(status[x](x.md)[y](y.md)[z](z.md) == ORANGE || status[x](x.md)[y](y.md)[z](z.md) == RED){







> }
> }//end top red

> }//end top y

> iterations++;
> }//end top x

> //end iterations on top half of square
> }

> //end Z
> }


> //end code, return byte..
> return stream;
}