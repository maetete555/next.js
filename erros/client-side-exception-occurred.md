# Client-side Exception Occurred

#### Why This Error Occurred

In your production application a client-side error occurred that was not caught by an error boundary. Additional information should be visible in the console tab of your browser.

#### Possible Ways to Fix It

Add error boundaries in your React tree to gracefully handle client-side errors and render a fallback view when they occur.

### Useful Links

- [Error Boundaries Documentation](https://reactjs.org/docs/error-boundaries.html)
- [Custom Error Page Documentation](https://nextjs.org/docs/advanced-features/custom-error-page#more-advanced-error-page-customizing)

<ErrorBoundary>
  <MyWidget />
</ErrorBoundary>
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }
    static getDerivedStateFromError(error) {
    // Update state so the next render will show the fallback UI.
    return { hasError: true };
  }
  componentDidCatch(error, errorInfo) {
    // You can also log the error to an error reporting service
    logErrorToMyService(error, errorInfo);
  }
    render() {
    if (this.state.hasError) {
      // You can render any custom fallback UI
      return <h1>Something went wrong.</h1>;
    }
        return this.props.children; 
  }
}
