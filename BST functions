package Project2;

/**
class1
 */
public class UnderflowException extends RuntimeException
{
    /**
     * Construct this exception object.
     */
    public UnderflowException( )
    {
        System.out.print("wrong");
    }
}

/**
class2
 */
 
import java.util.ArrayList;

//********************************** PART1: original code ********************************************
public class BinarySearchTree<AnyType extends Comparable<? super AnyType>>  //widecard
{
private BinaryNode<AnyType> root; 		//field
public BinarySearchTree( ) {  	  		//constructor
     root = null;
 }
private static class BinaryNode<AnyType> //Basic node stored in unbalanced binary search trees
{	
	AnyType element;            // The data in the node
	BinaryNode<AnyType> left;   // Left child
	BinaryNode<AnyType> right;  // Right child
	
	BinaryNode( AnyType theElement ){		  // Constructors  
       this( theElement, null, null );
   }
	
   BinaryNode( AnyType theElement, BinaryNode<AnyType> lt, BinaryNode<AnyType> rt )
   {
       element  = theElement;
       left     = lt;
       right    = rt;
   }
}

 //**********************************insert

 public void insert( AnyType x )
 {
     root = insert( x, root );
 }

 private BinaryNode<AnyType> insert( AnyType x, BinaryNode<AnyType> t )
 {
     if( t == null )
         return new BinaryNode<>( x, null, null );
     
     int compareResult = x.compareTo( t.element ); //compareTo equal 0, 1st greater >0, 2nd greater <0
         
     if( compareResult < 0 )
         t.left = insert( x, t.left );
     else if( compareResult > 0 )
         t.right = insert( x, t.right );
     else
         ;  // Duplicate; do nothing
     return t;
 }
//**********************************remove

 public void remove( AnyType x )
 {
     root = remove( x, root );
 }

 private BinaryNode<AnyType> remove( AnyType x, BinaryNode<AnyType> t )
 {
     if( t == null )
         return t;   // Item not found; do nothing
         
     int compareResult = x.compareTo( t.element );
         
     if( compareResult < 0 )
         t.left = remove( x, t.left );
     else if( compareResult > 0 )
         t.right = remove( x, t.right );
     else if( t.left != null && t.right != null ) // Two children
     {
         t.element = findMin( t.right ).element;
         t.right = remove( t.element, t.right );
     }
     else
         t = ( t.left != null ) ? t.left : t.right;
     return t;
 }
 //**********************************findMin
 public AnyType findMin( )
 {
     if( isEmpty( ) )
         throw new UnderflowException( );
     return findMin( root ).element;
 }
 private BinaryNode<AnyType> findMin( BinaryNode<AnyType> t )
 {
     if( t == null )
         return null;
     else if( t.left == null )
         return t;
     return findMin( t.left ); /* use recursion in return  */ 
 }

 //**********************************findMax

 public AnyType findMax( )
 {
     if( isEmpty( ) )
         throw new UnderflowException( );
     return findMax( root ).element;
 }

 private BinaryNode<AnyType> findMax( BinaryNode<AnyType> t )
 {
     if( t != null )
         while( t.right != null )
             t = t.right;

     return t;
 }
 //**********************************contains
 public boolean contains( AnyType x )
 {
     return contains( x, root );
 }
 
 private boolean contains( AnyType x, BinaryNode<AnyType> t )
 {
     if( t == null )
         return false;
         
     int compareResult = x.compareTo( t.element );
         
     if( compareResult < 0 )
         return contains( x, t.left ); //use recursion to find out 
     else if( compareResult > 0 )
         return contains( x, t.right );
     else //compareResult = 0 
         return true;    // Match
 }
 //**********************************makeEmpty

 public void makeEmpty( )
 {
     root = null;
 }
 //**********************************isEmpty

 public boolean isEmpty( )
 {
     return root == null;
 }
 //**********************************printTree

 public void printTree( )
 {
     if( isEmpty( ) )
         System.out.println( "Empty tree" );
     else
         printTree( root );
 }
 private void printTree( BinaryNode<AnyType> t ) //print in order
 {
     if( t != null )
     {
         printTree( t.left );
         System.out.println( t.element );
         printTree( t.right );
     }
 }
 //**********************************height

 private int height( BinaryNode<AnyType> t )
 {
     if( t == null )
         return -1;
     else
         return 1 + Math.max( height( t.left ), height( t.right ) );    
 }


//********************************** PART2: personal code ********************************************
 
 //a) nodeCount
 public int nodeCount( )
 {   
	 if( isEmpty( ) )
         return 0;
     else 
    	 return nodeCount(root);
 }
 public int nodeCount(BinaryNode<AnyType> n) {
	 if (n==null)
		 return 0;
	 else
	 return 1+ nodeCount(n.left)+nodeCount(n.right);
 }
 
 //b) isFull
 public boolean isFull() {
	 return isFull(root);
 }
 public boolean isFull(BinaryNode<AnyType> n) {

	    if (n==null)
	        return true;
	    if (n.left==null && n.right==null)
	        return true;
	    if((n.left==null) ^ (n.right==null)) 
	        return false; 
	        	    
	    return isFull(n.left) && isFull(n.right);  

	 }
 
 //c) compareStructure
// public boolean compareStructure(BinaryNode<AnyType> n) {    //below will pass parameter directly 
//	 return compareStructure(root, n );
// }
 public boolean compareStructure(BinaryNode<AnyType> n1, BinaryNode<AnyType> n2 ) {

	 if(n1==null&&n2==null) {
		 return true;
	 }
	 if ((n1==null)^(n2==null)) {
		 return false;
	 }
	 return compareStructure(n1.left,n2.left)&&compareStructure(n1.right,n2.right);
	 
 }
 
 //d) equals
public boolean equals(BinaryNode<AnyType> n1, BinaryNode<AnyType> n2 ) {
	if (n1==null && n2==null) {
		return true;
	}
	if (n1==null^n2==null) {
		return false;
	}
	return n1.element==n2.element && equals(n1.left,n2.left)&& equals(n1.right,n2.right);	
	
 }

//e) copy
public BinarySearchTree<AnyType> copy(BinarySearchTree<AnyType> newTree){//copy the original tree, return new one
	newTree.root=this.root;
	return newTree;
}

//f) mirror
public BinarySearchTree<AnyType> mirror(BinarySearchTree<AnyType> newTree){//mirror the original tree, return new one
	BinaryNode<AnyType> current = this.root;
	BinaryNode<AnyType> newMirror=mirrorNode(current);
	newTree.root=newMirror;
	return newTree;
}
//   method1----result is the same as method2, but the pointer is wrong, should use the method 2
/*
	public BinaryNode<AnyType> mirrorNode(BinaryNode<AnyType> current ) {
	if (current ==null) { //base
		return null;
	}
	BinaryNode<AnyType> left = mirrorNode(current.left); //post order mirror
	BinaryNode<AnyType> right= mirrorNode(current.right);
	current.right= left;
	current.left=right;
	return current;
}
 */ 
//   method2:

	public BinaryNode<AnyType> mirrorNode(BinaryNode<AnyType> current ){
		if (current ==null) { //base
			return null;
		}
		return new BinaryNode<AnyType>(current.element,mirrorNode(current.right),mirrorNode(current.left) );
	}

//g) isMirror
public boolean isMirror(BinaryNode<AnyType> n1, BinaryNode<AnyType> n2 ) {
	if (n1==null && n2==null) {
		return true;
	}
	if (n1==null^n2==null) {
		return false;
	}
	return (n1.element==n2.element) && isMirror(n1.left,n2.right)&& isMirror(n1.right,n2.left);
}
//h1) rotateRight a little similar to remove
public BinaryNode<AnyType> rotateRight(BinaryNode<AnyType> n){
    if( isEmpty( ) )
        throw new UnderflowException( );
	BinaryNode<AnyType> left = n.left;
	n.left= left.right;
	left.right=n;
	return left;
}

//h2) rotateLeft 
public BinaryNode<AnyType> rotateLeft(BinaryNode<AnyType> n){
    if( isEmpty( ) )
        throw new UnderflowException( );
	BinaryNode<AnyType> right = n.right;
	n.right= right.left;
	right.left=n;	
	return right;
}

//i) printLevels
private void printLevels( BinaryNode<AnyType> root ) {
	ArrayList<BinaryNode<AnyType>> nodes = new ArrayList<BinaryNode<AnyType>>();
	allNodes(root, nodes);
	int h=height(root);
	
	for (int j=0; j<h+1; j++) {
		for (BinaryNode<AnyType> i: nodes) {
			if (height(i)==j) {
				System.out.println("height"+j+ "  Node"+ i.element);
			}
		}
	}
}
public BinaryNode<AnyType> allNodes(BinaryNode<AnyType> n, ArrayList<BinaryNode<AnyType>> nodes){
	nodes.add(n);
	if (n== null) {
		return null;
	}
	allNodes(n.left,nodes);
	allNodes(n.right,nodes);
	return n;
}

// find and return node with certain element 
private BinaryNode<AnyType> find( AnyType x, BinaryNode<AnyType> t )
{
    if( t == null )
        return t;   // Item not found; do nothing
        
    int compareResult = x.compareTo( t.element );
        
    if( compareResult < 0 )
    	return find( x, t.left );
    else if( compareResult > 0 )
    	return find( x, t.right );
    else 
    return t;
}

 
//Test program
 public static void main( String [ ] args )
 {
	 //----------- j) test methods 
	 //full: tree
	 //two ways to create a tree: 1)tree-one by one 2)tree1--insert element from an array 
	 BinarySearchTree<Integer> tree = new BinarySearchTree<>( );	
     tree.root = new BinaryNode<>(50); 
     tree.root.left = new BinaryNode<>(20); 
     tree.root.right = new BinaryNode<>(70); 
     tree.root.left.left = new BinaryNode<>(10); 
     tree.root.left.right = new BinaryNode<>(35); 
     tree.root.right.left = new BinaryNode<>(60); 
     tree.root.right.right = new BinaryNode<>(80); 
     
    //not full: tree1
	 BinarySearchTree<Integer> tree1 = new BinarySearchTree<>( );
	 int[] arr1 = {50,20,70,10,35,60,80,5,25,30};
	 for (int i: arr1) {
		 tree1.insert(i);
	 }
	 //tree1=tree2
	 BinarySearchTree<Integer> tree2 = new BinarySearchTree<>( );
	 int[] arr2 = {50,20,70,10,35,60,80,5,25,30};  
	 for (int i: arr2) {
		 tree2.insert(i);
	 }
	 //new tree for copy and mirror and rotate: tree3
	 BinarySearchTree<Integer> tree3 = new BinarySearchTree<>( );
	 
	   //a) nodeCount
     int nc = tree1.nodeCount();
     System.out.println("nodeCount for tree1----"+nc+"\n");
     //b) isFull
     System.out.println("isFull function for tree----"+tree.isFull());
     System.out.println("isFull function for tree1----"+tree1.isFull()+"\n");
     //c) compareStructure
     System.out.println("compareStructure function for tree1 and tree2----"+tree1.compareStructure(tree1.root,tree2.root));
     System.out.println("compareStructure function for tree1 and tree----"+tree.compareStructure(tree1.root,tree.root)+"\n");
     //d) equals
     System.out.println("equals function for tree1 and tree2----"+tree.equals(tree1.root,tree2.root));
     System.out.println("equals function for tree1 and tree----"+tree.equals(tree1.root,tree.root)+"\n");
     //e) copy
     tree3=tree.copy(tree3);
     System.out.println("tree3 copies tree----"+"(print tree in order)");
     tree3.printTree(tree3.root);
     System.out.println("\n");
     //f) mirror
     tree3=tree.mirror(tree3);
     System.out.println("tree3 mirrors tree----"+"(print tree in order)");
     tree3.printTree(tree3.root);
     System.out.println("\n");
     //g) isMirror
     System.out.println("isMirror function for tree and tree3----"+"( should be mirror)" + "\n"+tree.isMirror(tree.root,tree3.root) +"\n");
     //h) rotateRight     
     tree3.root=tree3.rotateRight(tree3.root);
     System.out.println("rotateRight--root is"+ tree3.root.element+" (print tree in order)");
     tree3.printTree(tree3.root);
     System.out.println("print same tree by height");
     tree3.printLevels(tree3.root);
     System.out.println("\n");  
     //h) rotateLeft  now based on tree3 root is 70
     tree3.root=tree3.rotateLeft(tree3.root);
     System.out.println("rotateLeft--root is"+ tree3.root.element+" (print tree in order)");
     tree3.printTree(tree3.root);
     System.out.println("\n");  
     //i) printLevels
     System.out.println("printLevels for tree----");
     tree.printLevels(tree.root);
     System.out.println("\n");  

     BinarySearchTree<Integer> t = new BinarySearchTree<>( );
     final int NUMS = 4000;
     final int GAP  =   37;

     System.out.println( "Checking... (no more output means success)" );

     for( int i = GAP; i != 0; i = ( i + GAP ) % NUMS )
         t.insert( i );

     for( int i = 1; i < NUMS; i+= 2 )
         t.remove( i );

     if( NUMS < 40 )
         t.printTree( );
     
     if( t.findMin( ) != 2 || t.findMax( ) != NUMS - 2 )
         System.out.println( "FindMin or FindMax error!" );

     for( int i = 2; i < NUMS; i+=2 )
          if( !t.contains( i ) )
              System.out.println( "Find error1!" );

     for( int i = 1; i < NUMS; i+=2 )
     {
         if( t.contains( i ) )
             System.out.println( "Find error2!" );
     }
 }
}
