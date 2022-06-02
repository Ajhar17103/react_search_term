# react_search_term

function Search() {
  const [product, setProduct] = useState([]);
  const [searchTerm, setSearchTerm] = useState('')

  useEffect(()=>{
    axios.get("https://shop.hoolo.live/api/allproducts")
    .then(res=>{
      setProduct(res.data)
    })
  },[])
  return (
  
    <div className="m-5">
       <input type="text" placeholder="Search..." onChange={(e)=>setSearchTerm(e.target.value)} />

     <div>
      {product.filter((product)=>{
        if(searchTerm==""){
          return product
        }else if(product.slug.toLowerCase().includes(searchTerm.toLocaleLowerCase())){
          return product
        }
      }).map((product,index)=>(

       <h1 key={index}>{product.slug}</h1>

      ))}
    </div>
    </div>
   
   
  )
}

export default Search;
