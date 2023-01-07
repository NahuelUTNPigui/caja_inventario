<script>
    import {Col,Container,Row} from 'sveltestrap'
    import {Router,Link} from 'svelte-routing'
    export let url = ""
</script>
<Container>
    <Router url="{url}">
        <nav>
            <Row>
                <Col>
                    <Link to="/">Home</Link>
                </Col>

                <Col>
                    <Link to="/clientes"> Clientes</Link>
                </Col>
                <Col>
                    <Link to="/proveedores"> Proveedores</Link>
                </Col>
                <Col>
                    <Link to="/productos">Productos</Link>
                </Col>
                <Col>
                    <Link to="/ventas"> Ventas</Link>
                </Col>
                <Col>
                    <Link to="/compras"> Compras</Link>
                </Col>
                <Col>
                    <Link to="/ingresos"> Ingresos</Link>
                </Col>
                <Col>
                    <Link to="/egresos"> Egresos</Link>
                </Col>
                <Col>
                    <Link to="/reportes"> Reportes</Link>
                </Col>
            </Row>
        </nav>
    </Router>
</Container>