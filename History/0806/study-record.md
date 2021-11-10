- 양혜진
    
    [5. Algorithms](https://www.notion.so/5-Algorithms-dd7b0cf55e3842c3acd0e74a565c5203) 
    
- 김수연
    
    [소수 찾기 알고리즘: 에라토스테네스의 체](https://alveloper.oopy.io/0a1dbcdd-ed24-4fbc-a6a0-13b24fdc68da)
    
- 윤수진
    
    바닐라 JS의 한계?!
    
    1. 정적 페이지를 만들다 보면 똑같은 UI여도 계속 똑같은 코드를 만들어야 함(재사용 불가)
    
    2. 웹앱이 점점 커질수록, 관리해야 하는 element와 event가 많아짐(복잡도 증가)
    
    > 리액트 등장 > 리액트는 처음부터 다 다시 그린다 > Virtual DOM 사용해서 효율적으로 구현
    > 
    - 리액트는 **불변성**이 중요~!
    - 절대로. state를. 직접. 바꾸지. 말라.
    
    : 값만 바꿔버리면 리액트가 변화를 감지할 수 없어서 리렌더링이 되지 않기 때문
    
    const Haha = () => {
    
    const [merong, setMerong] = useState([]);
    
    불변성을 지키기 위해
    
    setMerong(['merong']); => setter
    
    merong = merong.push('merong'); => 레퍼런스 주소가 그대로 -> 바뀐걸 감지 x
    
- C++로 구현한 리스트 컨테이너
    - List.hpp
        
        ```cpp
        #ifndef LIST_HPP
        # define LIST_HPP
        
        # include <memory>
        # include <limits>
        # include "ListIterator.hpp"
        # include "../utils.hpp"
        
        namespace ft
        {
        	template <class T, class Alloc=std::allocator<T> >
        	class List
        	{
        		public:
        			typedef T value_type;
        			typedef Alloc allocator_type;
        			typedef T& reference;
        			typedef const T& const_reference;
        			typedef T* pointer;
        			typedef const T* const_pointer;
        			typedef ft::ListIterator<T> iterator;
        			typedef ft::ConstListIterator<T> const_iterator;
        			typedef ft::ReverseListIterator<T> reverse_iterator;
        			typedef ft::ConstReverseListIterator<T> const_reverse_iterator;
        			typedef size_t size_type;
        
        		private:
        			Node<T>* _head;
        			Node<T>* _tail;
        			allocator_type _allocator;
        			size_type _length;
        
        			Node<T>* _make_new_node(Node<T> *prev, value_type value, Node<T> *next)
        			{
        				Node<T>* node = new Node<T>;
        				node->prev = prev;
        				node->data = value;
        				node->next = next;
        				return node;
        			}
        			void _init_list()
        			{
        				_head = _make_new_node(NULL, value_type(), NULL);
        				_tail = _make_new_node(_head, value_type(), NULL);
        				_head->next = _tail;
        			}
        			void _set_head_tail_node()
        			{
        				if (_length == 0)
        				{
        					_head->data = value_type();
        					_tail->data = value_type();
        				}
        				else if (_length == 1)
        				{
        					_tail->data = 1;
        					_head->data = _tail->data;
        				}
        				else
        				{
        					_tail->data = _tail->prev->data;
        					_head->data = _tail->data;
        				}
        			}
        			template <typename N>
        			bool _equal(const N& n1, const N& n2) {return n1 == n2;}
        
        		public:
        			explicit List(const allocator_type& alloc = allocator_type()) : _length(0)
        			{
        				(void)alloc;
        				_init_list();
        			}
        			explicit List(size_type n, const value_type& val, const allocator_type& alloc = allocator_type()) : _length(0)
        			{
        				(void)alloc;
        				_init_list();
        				assign(n, val);
        			}
        			template <class InputIterator>
        			List (InputIterator first, InputIterator last, const allocator_type& alloc = allocator_type()) : _length(0)
        			{
        				(void)alloc;
        				_init_list();
        				assign(first, last);
        			}
        			List (const List& n) : _length(0)
        			{
        				_init_list();
        				assign(n.begin(), n.end());
        				_length = n._length;
        			}
        			~List()
        			{
        				clear();
        				delete _head;
        				delete _tail;
        			}
        			List &operator=(const List &n)
        			{
        				clear();
        				assign(n.begin(), n.end());
        			}
        
        			iterator begin() {return iterator(_head->next);}
        			const_iterator begin() const {return const_iterator(_head->next);}
        			iterator end() {return iterator(_tail);}
        			const_iterator end() const {return const_iterator(_tail);}
        			
        			reverse_iterator rbegin() {return reverse_iterator(_tail->prev);}
        			const_reverse_iterator rbegin() const {return const_reverse_iterator(_tail->prev);}
        			reverse_iterator rend() {return reverse_iterator(_head);}
        			const_reverse_iterator rend() const {return const_reverse_iterator(_head);}
        			
        			bool empty() const {return (_length == 0);}
        			size_type size() const {return _length;}
        			size_type max_size() const {return (std::numeric_limits<size_type>::max() / (sizeof(Node<T>)));}
        
        			reference front() {return _head->next->data;}
        			const_reference front() const {return _head->next->data;}
        			reference back() {return _tail->prev->data;}
        			const_reference back() const {return _tail->prev->data;}
        
        			template <class InputIterator>
        			void assign(InputIterator first, InputIterator last)
        			{
        				clear();
        				while (first != last)
        				{
        					push_back(*first);
        					first++;
        				}
        			}
        			void assign(size_type n, const value_type& val)
        			{
        				clear();
        				while (n--)
        					push_back(val);
        			}
        			void push_front(const value_type& val)
        			{
        				Node<T>* new_node = _make_new_node(_head, val, _head->next);
        				_head->next->prev = new_node;
        				_head->next = new_node;
        				_length++;
        				_set_head_tail_node();
        			}
        			void pop_front()
        			{
        				Node<T>* after = _head->next->next;
        				delete _head->next;
        				after->prev = _head;
        				_head->next = after;
        				_length--;
        				_set_head_tail_node();
        			}
        			void push_back(const value_type& val)
        			{
        				Node<T>* new_node = _make_new_node(_tail->prev, val, _tail);
        				_tail->prev->next = new_node;
        				_tail->prev = new_node;
        				_length++;
        				_set_head_tail_node();
        			}
        			void pop_back()
        			{
        				Node<T>* before = _tail->prev->prev;
        				delete _tail->prev;
        				before->next = _tail;
        				_tail->prev = before;
        				_length--;
        				_set_head_tail_node();
        			}
        			iterator insert(iterator position, const value_type& val)
        			{
        				if (position == begin())
        				{
        					push_front(val);
        					return begin();
        				}
        				else if (position == end())
        				{
        					push_back(val);
        					return end();
        				}
        				Node<T>* after = position.getNode();
        				Node<T>* before = after->prev;
        				Node<T>* inserted_node = _make_new_node(before, val, after);
        				before->next = inserted_node;
        				after->prev = inserted_node;
        				_length++;
        				return iterator(inserted_node);
        			}
        			void insert(iterator position, size_type n, const value_type& val)
        			{
        				while (n--)
        					position = insert(position, val);
        			}
        			template <class InputIterator>
        			void insert(iterator position, InputIterator first, InputIterator last)
        			{
        				while (first != last)
        				{
        					position = insert(position, *first);
        					first++;
        					if (position != end())
        						++position;
        				}
        			}
        			iterator erase(iterator position)
        			{
        				if (position == begin())
        				{
        					pop_front();
        					return begin();
        				}
        				else if (position == end())
        				{
        					pop_back();
        					return end();
        				}
        				Node<T>* before = position.getNode()->prev;
        				Node<T>* after = position.getNode()->next;
        				delete position.getNode();
        				before->next = after;
        				after->prev = before;
        				_length--;
        				_set_head_tail_node();
        				return iterator(after);
        			}
        			iterator erase(iterator first, iterator last)
        			{
        				while (first != last)
        				{
        					erase(first);
        					first++;
        				}
        				return first;
        			}
        			void swap(List &n)
         		{
        				ft::swap(n._length, _length);
        				ft::swap(n._head, _head);
        				ft::swap(n._tail, _tail);
        			}
        			void resize(size_type n, value_type val = value_type())
        			{
        				while (_length > n)
        					pop_back();
        				while (_length < n)
        					push_back(val);
        			}
        			void clear()
        			{
        				Node<T>* node = _head->next;
        				while (node != _tail)
        				{
        					Node<T>* next = node->next;
        					delete node;
        					node = next;
        				}
        				_head->next = _tail;
        				_tail->prev = _head;
        				_length = 0;
        				_set_head_tail_node();
        			}
        			void splice(iterator position, List& n)
        			{
        				splice(position, n, n.begin(), n.end());
        			}
        			void splice(iterator position, List& n, iterator iter)
        			{
        				insert(position, *iter);
        				n.erase(iter);
        			}
        			void splice(iterator position, List& n, iterator first, iterator last)
        			{
        				insert(position, first, last);
        				n.erase(first, last);
        			}
        			void remove(const value_type& val)
        			{
        				iterator iter = begin();
        				while (iter != end())
        				{
        					if (*iter == val)
        						iter = erase(iter);
        					else
        						iter++;
        				}
        			}
        			template <class Predicate>
        			void remove_if (Predicate pred)
        			{
        				iterator iter = begin();
        				while (iter != end())
        				{
        					if (pred(*iter))
        						iter = erase(iter);
        					else
        						iter++;
        				}
        			}
        			void unique()
        			{
        				unique(this->_equal);
        			}
        			template <class BinaryPredicate>
        			void unique(BinaryPredicate binary_pred)
        			{
        				iterator iter = begin();
        				iterator next_iter = ++begin();
        				while (iter != --end())
        				{
        					if (binary_pred(*iter, *next_iter))
        						next_iter = erase(next_iter);
        					else
        					{
        						iter = next_iter;
        						next_iter++;
        					}
        				}
        			}
        			void merge(List& n)
        			{
        				if (&n == this)
        					return ;
        				insert(begin(), n.begin(), n.end());
        				n.clear();
        				sort();
        			}
        			template <class Compare>
        			void merge(List& n, Compare comp)
        			{
        				if (&n == this)
        					return ;
        				insert(end(), n.begin(), n.end());
        				n.clear();
        				for (iterator it = begin(); it != --end(); it++)
                        {
                            for (iterator next_it = it; next_it != end(); next_it++)
                            {
                                if (comp(*it, *next_it))
                                    ft::swap(*it, *next_it);
                            }
                        }
        			}
        			void sort()
        			{
        				for (iterator it = begin(); it != --end(); it++)
        				{
        					for (iterator next_it = it; next_it != end(); next_it++)
        					{
        						if (*it > *next_it)
        							ft::swap(*it, *next_it);
        					}
        				}
        			}
        			template <class Compare>
        			void sort(Compare comp)
        			{
        				for (iterator it = begin(); it != --end(); it++)
        				{
        					for (iterator next_it = it; next_it != end(); next_it++)
        					{
        						if (!comp(*it, *next_it))
        							ft::swap(*it, *next_it);
        					}
        				}
        			}
        			void reverse()
        			{
        				size_type i = 0;
        				iterator first = begin();
        				iterator last = --end();
        				while (i != _length / 2)
        				{
        					ft::swap(*first, *last);
        					first++;
        					last--;
        					i++;
        				}
        			}
        	};
        	
        	template <typename T>
        	bool operator==(List<T>& lhs, List<T>& rhs)
        	{
        		if (lhs.size() != rhs.size())
        			return false;
        		typename List<T>::iterator liter = lhs.begin();
        		typename List<T>::iterator riter = rhs.begin();
        		while (liter != lhs.end())
        		{
        			if (*liter != *riter)
        				return false;
        			liter++;
        			riter++;
        		}
        		return true;
        	}
        	template <typename T>
        	bool operator!=(List<T>& lhs, List<T>& rhs)
        	{
        		return !(lhs == rhs);
        	}
        	template <typename T>
        	bool operator<(List<T>& lhs, List<T>& rhs)
        	{
        		if (lhs.size() < rhs.size())
        			return true;
        		if (lhs.size() > rhs.size())
        			return false;
        		typename List<T>::iterator liter = lhs.begin();
        		typename List<T>::iterator riter = rhs.begin();
        		while (liter != lhs.end())
        		{
        			if (*liter != *riter)
        				return (*liter < *riter);
        			liter++;
        			riter++;
        		}
        		return false;
        	}
        	template <typename T>
        	bool operator<=(List<T>& lhs, List<T>& rhs)
        	{
        		return (!(rhs < lhs));
        	}
        	template <typename T>
        	bool operator>(List<T>& lhs, List<T>& rhs)
        	{
        		return (rhs < lhs);
        	}
        	template <typename T>
        	bool operator>=(List<T>& lhs, List<T>& rhs)
        	{
        		return (!(lhs < rhs));
        	}
        	template <typename T>
        	void swap(List<T>& n1, List<T>& n2)
        	{
        		n1.swap(n2);
        	}
        }
        
        #endif
        ```
        
    - ListIterator.hpp
        
        ```cpp
        #ifndef LISTITERATOR_HPP
        # define LISTITERATOR_HPP
        
        # include "../utils.hpp"
        # include <queue>
        namespace ft
        {
        	template <typename T>
        	class ListIterator
        	{
        		public:
        			typedef T			value_type;
        			typedef Node<T>*	pointer;
        			typedef T&			reference;
        
        		protected:
        			pointer				_ptr;
        
        		public:
        			ListIterator() {}
        			ListIterator(pointer ptr) : _ptr(ptr) {}
        			ListIterator(const ListIterator &ref) {*this = ref;}
        			~ListIterator() {}
        			ListIterator &operator=(const ListIterator &ref) {
        				_ptr = ref._ptr;
        				return (*this);
        			}
        
        			pointer getNode() const {return _ptr;}
        
        			bool operator==(const ListIterator &ref) const {return _ptr == ref._ptr;}
        			bool operator!=(const ListIterator &ref) const {return _ptr != ref._ptr;}
        			value_type &operator*() {return _ptr->data;}
        			value_type operator->() {return _ptr;}
        			ListIterator &operator++() { // prefix
        				_ptr = _ptr->next;
        				return *this;
        			}
        			ListIterator operator++(int) { // postfix
        				ListIterator temp(*this);
        				operator++();
        				return temp;
        			}
        			ListIterator &operator--() {
        				_ptr = _ptr->prev;
        				return *this;
        			}
        			ListIterator operator--(int) {
        				ListIterator temp(*this);
        				operator--();
        				return temp;
        			}
        	};
        
        	template <typename T>
        	class ReverseListIterator
        	{
        		public:
        			typedef T			value_type;
        			typedef Node<T>*	pointer;
        			typedef T&			reference;
        
        		protected:
        			pointer				_ptr;
        
        		public:
        			ReverseListIterator() {}
        			ReverseListIterator(pointer ptr) : _ptr(ptr) {}
        			~ReverseListIterator() {}
        			ReverseListIterator(const ReverseListIterator &ref) {*this = ref;}
        			ReverseListIterator &operator=(const ReverseListIterator &ref) {
        				_ptr = ref._ptr;
        				return *this;
        			}
        
        			bool operator==(const ReverseListIterator &ref) const {return _ptr == ref._ptr;}
        			bool operator!=(const ReverseListIterator &ref) const {return _ptr != ref._ptr;}
        			value_type &operator*() {return _ptr->data;}
        			value_type operator->() {return _ptr;}
        			ReverseListIterator &operator++() { // prefix
        				_ptr = _ptr->prev;
        				return *this;
        			}
        			ReverseListIterator operator++(int) { // postfix
        				ReverseListIterator temp(*this);
        				operator++();
        				return temp;
        			}
        			ReverseListIterator &operator--() {
        				_ptr = _ptr->next;
        				return *this;
        			}
        			ReverseListIterator operator--(int) {
        				ReverseListIterator temp(*this);
        				operator--();
        				return temp;
        			}
        	};
        
        	template <typename T>
        	class ConstListIterator
        	{
        		public:
        			typedef T			value_type;
        			typedef Node<T>*	pointer;
        			typedef T&			reference;
        
        		protected:
        			pointer				_ptr;
        
        		public:
        			ConstListIterator() {}
        			ConstListIterator(pointer ptr) : _ptr(ptr) {}
        			ConstListIterator(const ConstListIterator &ref) {*this = ref;}
        			~ConstListIterator() {}
        			ConstListIterator &operator=(const ConstListIterator &ref) {
        				_ptr = ref._ptr;
        				return *this;
        			}
        
        			pointer getNode() const {return _ptr;}
        
        			bool operator==(const ConstListIterator &ref) const {return _ptr == ref._ptr;}
        			bool operator!=(const ConstListIterator &ref) const {return _ptr != ref._ptr;}
        			const value_type &operator*() {return _ptr->data;}
        			const value_type operator->() {return _ptr;}
        			ConstListIterator &operator++() {
        				_ptr = _ptr->next;
        				return *this;
        			}
        			ConstListIterator operator++(int) {
        				ConstListIterator tmp(*this);
        				operator++();
        				return tmp;
        			}
        			ConstListIterator &operator--() {
        				_ptr = _ptr->prev;
        				return (*this);
        			}
        			ConstListIterator operator--(int) {
        				ConstListIterator tmp(*this);
        				operator--();
        				return tmp;
        			}
        	};
        
        	template <typename T>
        	class ConstReverseListIterator
        	{
        		public:
        			typedef T	value_type;
        			typedef Node<T>*	pointer;
        			typedef T&			reference;
        
        		protected:
        			pointer				_ptr;
        
        		public:
        			ConstReverseListIterator() {}
        			ConstReverseListIterator(pointer ptr) : _ptr(ptr) {}
        			ConstReverseListIterator(const ConstReverseListIterator &ref) {*this = ref;}
        			ConstReverseListIterator &operator=(const ConstReverseListIterator &ref) {
        				_ptr = ref._ptr;
        				return *this;
        			}
        			~ConstReverseListIterator() {}
        
        			pointer getNode() const {return _ptr;}
        
        			bool operator==(const ConstReverseListIterator &ref) const {return _ptr == ref._ptr;}
        			bool operator!=(const ConstReverseListIterator &ref) const {return _ptr != ref._ptr;}
        			const value_type &operator*() {return _ptr->data;}
        			const value_type operator->() {return _ptr;}
        			ConstReverseListIterator &operator++() {
        				_ptr = _ptr->prev;
        				return *this;
        			}
        			ConstReverseListIterator operator++(int) {
        				ConstReverseListIterator tmp(*this);
        				operator++();
        				return tmp;
        			}
        			ConstReverseListIterator &operator--() {
        				_ptr = _ptr->next;
        				return *this;
        			}
        			ConstReverseListIterator operator--(int) {
        				ConstReverseListIterator tmp(*this);
        				operator--();
        				return tmp;
        			}
        	};
        }
        
        #endif
        ```
