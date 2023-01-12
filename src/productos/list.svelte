<script>
    import { Link, navigate, Router } from 'svelte-routing';
    import {Container,Row,Col,Button,Table,Input,Modal,ModalBody,ModalFooter,ModalHeader} from 'sveltestrap'
    import {ruta} from '../store'
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    export let url=""
    let nombre = ""
    let precio_venta=""
    let cantidad = ""
    let open = false
    const toggle = ()=>{open = !open}
    function nuevo_producto(){
        navigate('/detalleproducto')
    }
    async function eliminarProducto(){

        toggle()
    }
    let productos = [{cliente:"nahuel",monto:'555',fecha:'12/05/2022'},]
</script>
<div>
    <Modal isOpen={open} {toggle}>
      <ModalHeader {toggle}>Eliminar producto</ModalHeader>
      <ModalBody>
        Esta seguro que desea eliminar el ingreso?.
        <br>
        Podria modificar informacion en el stock y la caja
      </ModalBody>
      <ModalFooter>
        <Button color="danger">Eliminar</Button>
        <Button color="secondary">Cancel</Button>
      </ModalFooter>
    </Modal>
</div>