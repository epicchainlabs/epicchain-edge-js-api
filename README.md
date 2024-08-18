# EpicChain EdgeJS API

## Overview

**EpicChain-EdgeJS-API** is an advanced integration framework that connects EpicChain's blockchain functionalities with Node.js applications using Edge.js. This repository enables smooth execution of C# code from within a Node.js environment, allowing developers to leverage EpicChain's blockchain capabilities and integrate them with various external systems and services.

### Key Features
- **Node.js and .NET Integration:** Seamlessly execute C# code from Node.js applications.
- **Flexible API Layer:** Interact with EpicChain’s smart contracts and services via a structured API.
- **Cross-Platform Compatibility:** Operates on any platform where Node.js and .NET Core are supported.

## Configuration

To utilize the API effectively, you'll need to set up configuration parameters for Edge.js and EpicChain. Ensure you have the following environment variables and configuration settings in place:

- **EPICCHAIN_API_URL**: Specifies the URL endpoint for the EpicChain API. This should point to the location where your EpicChain services are hosted.
- **EDGE_NET_DLL_PATH**: The path to the .NET assembly (.dll) that Edge.js will utilize. This assembly contains the C# methods you want to call from Node.js.

Here’s an example `.env` configuration file:

```env
EPICCHAIN_API_URL=http://localhost:5000/api
EDGE_NET_DLL_PATH=./path/to/your/csharp/assembly.dll
```

## Usage

The EpicChain-EdgeJS-API provides a range of functionalities to interact with EpicChain. Below, you'll find detailed examples demonstrating how to utilize the API for various operations.

### Basic Setup

Initialize Edge.js to integrate with your C# assembly:

```javascript
const edge = require('edge');

const epicChainApi = edge.func({
  assemblyFile: process.env.EDGE_NET_DLL_PATH,
  typeName: 'EpicChainApi',
  methodName: 'CallMethod'
});
```

In the configuration above:
- `assemblyFile` points to the .NET DLL file.
- `typeName` specifies the C# class containing the methods you wish to call.
- `methodName` indicates the method in the C# class to be invoked.

### Example 1: Querying EpicChain Data

To query data from EpicChain, you can call a method in your C# assembly as follows:

```javascript
epicChainApi('QueryEpicChainData', { queryParam: 'value' }, (error, result) => {
  if (error) {
    console.error('Error:', error);
  } else {
    console.log('Data:', result);
  }
});
```

In this example:
- `'QueryEpicChainData'` is the method in your C# assembly.
- `{ queryParam: 'value' }` is the object containing parameters required by the C# method.
- The callback function handles the result or error.

### Example 2: Submitting Transactions

For submitting transactions to the EpicChain network:

```javascript
epicChainApi('SubmitTransaction', { transactionData: 'data' }, (error, result) => {
  if (error) {
    console.error('Transaction Error:', error);
  } else {
    console.log('Transaction Result:', result);
  }
});
```

In this example:
- `'SubmitTransaction'` is a method in the C# assembly designed to handle transaction submissions.
- `{ transactionData: 'data' }` includes the transaction details to be sent.

### Example 3: Handling Responses

To handle and process responses from EpicChain:

```javascript
epicChainApi('HandleResponse', { responseId: '123' }, (error, result) => {
  if (error) {
    console.error('Response Handling Error:', error);
  } else {
    console.log('Processed Response:', result);
  }
});
```

Here:
- `'HandleResponse'` is a method that processes responses received from EpicChain.
- `{ responseId: '123' }` represents the ID or data associated with the response.

## Contributing

Contributions to EpicChain-EdgeJS-API are welcome! If you have ideas for improvements or new features, please follow these steps:

1. **Fork the Repository:** Create your own fork of the repository.
2. **Clone Your Fork:** Clone your fork to your local development environment.
3. **Create a Branch:** Develop your feature or fix on a new branch.
4. **Submit a Pull Request:** Push your changes to your fork and submit a pull request.

## License

EpicChain-EdgeJS-API is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contact

For support or inquiries, please contact the maintainers at [support@epic-chain.org](mailto:support@epic-chain.org).
