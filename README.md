<style>
    .app-container {
        width: 350px;
        height: 260px;
    }

    .calculator {
        display: grid;
        grid-template-columns: repeat(4, auto);
        grid-template-rows: repeat(5, auto);
    }

    .display {
        grid-column-start: 1;
        grid-column-end: 5;
        text-align: right;
        border: 1px solid black;
        padding-top: 5px;
        padding-left: 10px;
        height: 50px;
    }

    button {
        height: 50px;
        background-color: rgb(8, 130, 151);
        border: 1px solid rgb(235, 244, 245);
    }

    button.operator {
        background-color: rgb(231, 231, 231);
    }
</style>
<div id="app"></div>

<script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

<script type="text/babel">
    // function sample(a, b){
    //     return console.log(a + b);
    // }

    // sample(2, 4);

    // // arrow function
    // const Add = (a, b) => (
    //     console.log(a + b)
    // )
    // add(3,4)

    // const name = 'Ryan';
    //   const hello = React.createElement("h1", {}, "Hello, React!");

    // const hello = (
    //     <div>
    //         <h3>Hello World!</h3>
    //     </div>
    // )
    //ReactDOM.render(hello, document.getElementById("app"));
    // #############################################################
    // Components
    // const Hello = (props) => (
    //     <h1>Hello, {props.name}, I am {props.age} years old!</h1>

    // )

    // ReactDOM.render(<Hello name='Bryan' age={12}/>, document.getElementById("app"));

    //===============================================================================================
    //React callback function


    // for the onCLick event

    // parent component
    function Calculator() {

        function handleNumber(value) {

            let newValue = value;
            if (!calc.isInitial) {
                newValue = calc.current + value;
            }
            setCalc({ current: newValue, isInitial: false });
        }

        const [calc, setCalc] = React.useState({
            current: '0',
            total: '',
            isInitial: true,
            preOp: ''
        });

        return (
            <div className="calculator">
                <div className="display">{calc.current}</div>

                <CalcButton value="7" onClick={handleNumber} />
                <CalcButton value="8" onClick={handleNumber} />
                <CalcButton value="9" onClick={handleNumber} />
                <CalcButton className="operator" value="*" />

                <CalcButton value="4" onClick={handleNumber} />
                <CalcButton value="5" onClick={handleNumber} />
                <CalcButton value="6" onClick={handleNumber} />
                <CalcButton className="operator" value="/" />

                <CalcButton value="1" onClick={handleNumber} />
                <CalcButton value="2" onClick={handleNumber} />
                <CalcButton value="3" onClick={handleNumber} />
                <CalcButton className="operator" value="+" />

                <CalcButton value="C" />
                <CalcButton value="0" onClick={handleNumber} />
                <CalcButton className="operator" value="=" />
                <CalcButton className="operator" value="-" />
            </div>
        );
    }
    // child component
    function CalcButton(props) {
        return (
            <button className={props.className} onClick={() => props.onClick(props.value)}>{props.value}</button>
        );
    }
    ReactDOM.render(<div className="app-container"><Calculator /></div>, document.getElementById("app"));
</script>
